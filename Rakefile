desc "Generate & Preview"
task :preview do
	system("compass compile --css-dir source/assets/css")
	jekyllPid = Process.spawn("jekyll serve --watch")
	compassPid = Process.spawn("compass watch")

	trap("INT") {
		[jekyllPid, compassPid].each { |pid| Process.kill(9, pid) rescue Errno::ESRCH }
		exit 0
	}

	[jekyllPid, compassPid].each { |pid| Process.wait(pid) }
end