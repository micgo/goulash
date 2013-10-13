#!/usr/bin/env rake

sandbox = File.join(File.dirname(__FILE__), %w{tmp cookbook})
prepare_sandbox(sandbox)

desc "Runs foodcritic"
task :foodcritic do
  if Gem::Version.new("1.9.2") <= Gem::Version.new(RUBY_VERSION.dup)
    sh "foodcritic --epic-fail any #{File.dirname(sandbox)}"
  else
    puts "WARN: foodcritic run is skipped as Ruby #{RUBY_VERSION} is < 1.9.2."
  end
end

desc "Runs ChefSpec"
task :foodcritic do
  if Gem::Version.new("1.9.2") <= Gem::Version.new(RUBY_VERSION.dup)
    sh "rspec #{File.dirname(sandbox)}"
  else
    puts "WARN: chefspec run is skipped as Ruby #{RUBY_VERSION} is < 1.9.2."
  end
end

task :default => [ :foodcritic, :chefspec ]

private

def prepare_sandbox(sandbox)
  files = %w{*.md *.rb attributes definitions files libraries providers recipes resources templates}
  rm_rf sandbox
  mkdir_p sandbox
  cp_r Dir.glob("{#{files.join(',')}}"), sandbox
  puts "\n\n"
end
