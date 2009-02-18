require 'rubygems'
require 'spec/rake/spectask'


begin
  require 'jeweler'
  Jeweler::Tasks.new do |s|
    s.name         = "email_spec"
    s.platform     = Gem::Platform::RUBY
    s.authors      = ['Ben Mabey', 'Aaron Gibralter', 'Mischa Fierer']
    s.email        = "ben@benmabey.com"
    s.homepage     = "http://github.com/bmabey/email-spec/"
    s.summary      = "Easily test email in rspec and cucumber"
    s.bindir       = "bin"
    s.description  = s.summary
    s.require_path = "lib"
    s.files        = %w(History.txt install.rb MIT-LICENSE.txt README.rdoc Rakefile) + Dir["lib/**/*"] + Dir["generators/**/*"] + Dir["spec/**/*"] + Dir["examples/**/*"]
    # rdoc
    s.has_rdoc         = true
    s.extra_rdoc_files = %w(README.rdoc MIT-LICENSE.txt)
  end
rescue LoadError
  puts "Jeweler not available. Install it with: sudo gem install technicalpickles-jeweler -s http://gems.github.com"
end

# Testing

desc "Run the generator on the tests"
task :generate do
  system "mkdir -p examples/rails_root/vendor/plugins/email_spec"
  system "cp -R generators examples/rails_root/vendor/plugins/email_spec"
  system "cd examples/rails_root; ./script/generate email_spec"
end

task :features => [:generate] do
  system("cucumber examples/rails_root/features")
end

task :default => :features

