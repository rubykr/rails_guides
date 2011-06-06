require 'rubygems'

desc "make Korean rails guide"
task :make_guides do 
  cur_path = File.expand_path("..",__FILE__)
  doc_path = File.expand_path("lib/docrails/railties/guides/output/ko-KR", cur_path)
  bun_path = File.expand_path("../rails_guides-bundle/")
  log = ""

  Dir.chdir cur_path do
    system("git pull")
    system("git submodule init;git submodule update")
  end

  Dir.chdir 'lib/docrails' do 
    system("git checkout master")
    system("git pull")
    system("bundle install --path #{bun_path}")
    system("cd railties;bundle exec rake  generate_guides GUIDES_LANGUAGE=ko-KR")
  end

  system("cp -R #{doc_path}/* #{cur_path}")

  Dir.chdir cur_path do
    system(%Q[git commit -a -m #{"auto update #{log}".inspect}])
    system("git push")
  end
end
