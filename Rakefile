begin
  require 'jeweler'
  require './lib/netzke/core/version'
  Jeweler::Tasks.new do |gemspec|
    gemspec.version = Netzke::Core::Version::STRING
    gemspec.name = "netzke-core"
    gemspec.summary = "Build ExtJS/Rails components with minimum effort"
    gemspec.description = "Allows building DRY ExtJS/Rails applications by enabling modular development"
    gemspec.email = "nmcoder@gmail.com"
    gemspec.homepage = "http://netzke.org"
    gemspec.authors = ["Denis Gorin"]
    gemspec.add_dependency("activesupport", ">=3.0.0")
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end


require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/*_test.rb'
  test.verbose = true
end

begin
  require 'rdoc/task'
rescue LoadError
  require 'rake/rdoctask'
end
Rake::RDocTask.new do |rdoc|
  require './lib/netzke/core/version'
  version = Netzke::Core::Version::STRING

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "netzke-core #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('CHANGELOG*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

namespace :rdoc do
  desc "Publish rdocs"
  task :publish => :rdoc do
    `scp -r rdoc/* fl:www/api.netzke.org/core`
  end
end
