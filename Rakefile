require 'rubygems'

desc "make Korean rails guide"
task :make_guides do 
  cur_path = File.expand_path("..",__FILE__)
  doc_path = File.expand_path("docrails/railties/guides/output/ko-KR", cur_path)

  Dir.chdir cur_path do
    system("git pull")
    system("git submodule init;git submodule update")
  end

  Dir.chdir 'docrails' do 
    system("git pull")
    system("bundle install --path vendor/bundle")
    system("cd railties;bundle exec rake  generate_guides LANGUAGE=ko-KR")
  end

  system("cp -R #{doc_path}/* #{cur_path}")

  Dir.chdir cur_path do
    system("git commit -a -m 'update source'")
    system("git push")
  end
end
