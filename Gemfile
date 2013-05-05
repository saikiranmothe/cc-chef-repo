#!/usr/bin/env ruby
#^syntax detection
################################################################################
def gem_dev(gem_name, *args)
  verbose = (ENV['VERBOSE'] == "1")
  gemdev = (ENV['GEMDEV'] == "1")

  if (File.exists?(path = File.join("vendor", "checkouts", gem_name)) && gemdev)
    if (arg = args.first{ |arg| arg.is_a?(Hash) })
      arg.reject!{ |k,v| [:git,:ref].include?(k) }
      arg.merge!(:path => path)
    else
      args << {:path => path}
    end
  end

  if verbose
    gem_details = args.collect{ |arg| arg.inspect }.join(", ")
    !gem_details.empty? and (gem_details = ", #{gem_details}")
    puts("%2sGEMDEV: %32s%s" % [((gemdev == true) ? "  " : "NO"), gem_name, gem_details])
  end

  gem(gem_name, *args)
end
################################################################################

source "https://rubygems.org"

# RUBYGEMS
###########
# gem "chef", "10.24.0"
# gem "chef", "11.4.0"
gem "chef"
gem "librarian-chef"

# DEVELOPMENT GEMS
###################
gem_dev "ztk"
gem_dev "cucumber-chef"
