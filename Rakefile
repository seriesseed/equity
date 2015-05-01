require 'rake'
require 'rake/clean'

markdown_files = Rake::FileList['*.md']
docx_files = markdown_files.ext('docx')
zip = 'Series Seed - Microsoft Word.zip'

task :default => zip

task zip => docx_files do |t|
  sh "zip '#{t.name}' " + t.prerequisites.map { |file| "'#{file}'" }.join(' ')
end

rule '.docx' => '.md' do |t|
  sh "pandoc -o '#{t.name}' '#{t.source}'"
end

CLEAN.include(docx_files)

CLOBBER << zip
