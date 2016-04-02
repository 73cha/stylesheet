require 'autoprefixer-rails'

guard 'livereload' do
  watch(%r{css/.+\.css})
  watch(%r{sass/.+\.scss})
  watch(%r{docs/.+\.html})
end

guard 'hologram', config_path: 'hologram_config.yml' do
  watch(%r{sass/.+\.scss})
  watch('hologram_config.yml')
end

# https://gist.github.com/alexdunae/c6ec418fb166fdebc42b
guard 'sass', input: 'sass', output: 'css', compass: false, smart_partials: true, all_on_start: true do
  callback(:run_on_changes_end) do |_, _, files|
    Array(files).each do |file|
      time = Benchmark.realtime { autoprefix_file(file) }
      benchmark = "[\e[33m%2.2fs\e[0m] " % time
      ::Guard::UI.info("\t\e[1;37mAutoprefixer\e[0m %s%s" % [benchmark, file])
    end
  end
end

def autoprefix_file(file)
  original_css = File.read(file)
  File.open(file, 'w') do |io|
    io << ::AutoprefixerRails.process(original_css, browsers: ['> 1%', 'ie >= 9'])
  end
end
