rule '.xrnx' => [ proc { |tn| tn[0..-6] } ] do |t|
    dir_name = File.basename(t.name, '.*')
    zip_name = dir_name + '.zip'
    xrnx_name = t.name

    sh "7z a #{zip_name} #{dir_name}/*"
    FileUtils.mv zip_name, xrnx_name
end

task :all => Dir.glob('*').select {|f| File.directory? f}.map{|f| f + '.xrnx'}
task :clean do |t|
    for f in Dir.glob '*.xrnx'
        FileUtils.rm f
    end
end

task :default => :all
