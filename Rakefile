require 'rubygems'

namespace :guides do
  desc "make Korean rails guide"
  task :make do 
    system("git submodule init;git submodule update")
    #system("git submodule foreach 'git pull'")
    Dir.chdir 'docrails' do 
      system("bundle install --path vendor/bundle")
      system("cd railties;bundle exec rake  generate_guides LANGUAGE=ko-KR")
    end

    cur_path = File.expand_path("..",__FILE__)
    doc_path = File.expand_path("docrails/railties/guides/output/ko-KR", cur_path)
    system("cp -R #{doc_path}/* #{cur_path}")
  end
end
