def jekyll(opts = "")
  sh "rm -rf _site"
  sh "jekyll " + opts
end

desc "Build site using Jekyll"
task :build do
  jekyll
end

desc "Serve on Localhost with port 4000"
task :default do
  jekyll("--server --auto")
end

task :stable do
  jekyll("--server --auto", "")
end


task :sass do
  # watch sara' disponibile nella prossima versione di sass
  # sh "sass --watch lib/sem4r.sass"
  sh "sass --update lib/sem4r.sass"
end

namespace :deploy do
  desc "Deploy to Dev"
  task :dev => :build do
    rsync "dev.sem4r.com"
  end
  
  desc "Deploy to Live"
  task :live => :build do
    rsync "sem4r.com"
  end
  
  desc "Deploy to Dev and Live"
  task :all => [:dev, :live]
  
  def rsync(domain)
    sh "rsync -rtz --delete _site/ sem4r@sem4r.com:~/#{domain}/"
  end
end

