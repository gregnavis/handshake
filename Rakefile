require 'rubygems'
require 'rake'
require 'rake/clean'
require 'rake/testtask'
require 'rake/packagetask'
require 'rake/gempackagetask'
require 'rake/rdoctask'
require 'rake/contrib/rubyforgepublisher'
require 'fileutils'
require 'hoe'

include FileUtils
require File.join(File.dirname(__FILE__), 'lib', 'handshake', 'version')

AUTHOR            = "Brian Guthrie"  # can also be an array of Authors
EMAIL             = "btguthrie@gmail.com"
DESCRIPTION       = "Handshake is a simple design-by-contract system for Ruby."
GEM_NAME          = "handshake" # what ppl will type to install your gem
RUBYFORGE_PROJECT = "handshake" # The unix name for your project
HOMEPATH          = "http://#{RUBYFORGE_PROJECT}.rubyforge.org"


NAME      = "handshake"
REV       = nil # UNCOMMENT IF REQUIRED: File.read(".svn/entries")[/committed-rev="(d+)"/, 1] rescue nil
VERS      = ENV['VERSION'] || (Handshake::VERSION::STRING + (REV ? ".#{REV}" : ""))
CLEAN.include ['**/.*.sw?', '*.gem', '.config']
RDOC_OPTS = ['--quiet', '--title', "Handshake documentation",
             "--opname", "index.html",
             "--line-numbers", 
             "--main", "README",
             "--inline-source"]

class Hoe
  def extra_deps 
    @extra_deps.reject { |x| Array(x).first == 'hoe' } 
  end 
end

# Generate all the Rake tasks
# Run 'rake -T' to see list of generated tasks (from gem root directory)
Hoe.new(GEM_NAME, VERS) do |p|
  p.author         = AUTHOR 
  p.description    = DESCRIPTION
  p.email          = EMAIL
  p.summary        = DESCRIPTION
  p.url            = HOMEPATH
  p.rubyforge_name = RUBYFORGE_PROJECT if RUBYFORGE_PROJECT
  p.test_globs = ["test/tc_*.rb"]
  p.clean_globs = CLEAN  #An array of file patterns to delete on clean.
  
  # == Optional
  #p.changes        - A description of the release's latest changes.
  #p.extra_deps     - An array of rubygem dependencies.
  #p.spec_extras    - A hash of extra values to set in the gemspec.
end
