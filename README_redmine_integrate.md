webhooks
--------


1. in repo settings: "Webhooks & Services" 

	"add webhooks": http://domain/github_hook?project_id=vimconfig

	```
Started POST "/github_hook?project_id=vimconfig" for 127.0.0.1 at 2014-02-18 15:20:33 +0800
Processing by GithubHookController#index as */*
  Parameters: {"project_id"=>"vimconfig", "payload"=>"{\"ref\":\"refs/heads/master\",\"after\":\"d6a16d513f9f668cffc96148cb5e162d5f0f03e3\",\"before\":\"77dc05ee683ac7f194671a80e810ec7bbcdf7873\",\"created\":false,\"deleted\":false,\"forced\":false,\"compare\":\"https://github.com/gankkank/vimConfig/compare/77dc05ee683a...d6a16d513f9f\",\"commits\":[{\"id\":\"d6a16d513f9f668cffc96148cb5e162d5f0f03e3\",\"distinct\":true,\"message\":\"clean\",\"timestamp\":\"2014-02-17T22:47:17-08:00\",\"url\":\"https://github.com/gankkank/vimConfig/commit/d6a16d513f9f668cffc96148cb5e162d5f0f03e3\",\"author\":{\"name\":\"gankkank\",\"email\":\"gankkank@gmail.com\",\"username\":\"gankkank\"},\"committer\":{\"name\":\"gankkank\",\"email\":\"gankkank@gmail.com\",\"username\":\"gankkank\"},\"added\":[\"trash\"],\"removed\":[],\"modified\":[]}],\"head_commit\":{\"id\":\"d6a16d513f9f668cffc96148cb5e162d5f0f03e3\",\"distinct\":true,\"message\":\"clean\",\"timestamp\":\"2014-02-17T22:47:17-08:00\",\"url\":\"https://github.com/gankkank/vimConfig/commit/d6a16d513f9f668cffc96148cb5e162d5f0f03e3\",\"author\":{\"name\":\"gankkank\",\"email\":\"gankkank@gmail.com\",\"username\":\"gankkank\"},\"committer\":{\"name\":\"gankkank\",\"email\":\"gankkank@gmail.com\",\"username\":\"gankkank\"},\"added\":[\"trash\"],\"removed\":[],\"modified\":[]},\"repository\":{\"id\":10192610,\"name\":\"vimConfig\",\"url\":\"https://github.com/gankkank/vimConfig\",\"description\":\"vim enhance scripts used (directory: ~/.vim).\",\"watchers\":1,\"stargazers\":1,\"forks\":0,\"fork\":false,\"size\":384,\"owner\":{\"name\":\"gankkank\",\"email\":\"gankkank@gmail.com\"},\"private\":false,\"open_issues\":0,\"has_issues\":true,\"has_downloads\":true,\"has_wiki\":true,\"language\":\"VimL\",\"created_at\":1369129950,\"pushed_at\":1392706051,\"master_branch\":\"master\"},\"pusher\":{\"name\":\"gankkank\",\"email\":\"gankkank@gmail.com\"}}"}
  Current user: anonymous
GithubHook: Command 'git --git-dir='repositories/vimconfig.git' fetch origin' didn't exit properly. Full output: ["fatal: Not a git repository: 'repositories/vimconfig.git'\n"]
  Rendered text template (0.0ms)
Completed 200 OK in 29.0ms (Views: 1.0ms | ActiveRecord: 0.0ms)

	```

**plugins** 

	```
  GIT_BIN = Redmine::Configuration['scm_git_command'] || "sudo git"
  def git_command(command, repository)
    GIT_BIN + " --git-dir='/opt/git/#{repository.url}' #{command}"
  end
	```


2. in redmine repo

	su git
	git clone --mirror git@github.com:git_user/project.git
	cd project.git
	git fetch -q --all

	git fetch -v
	git fetch -v origin

Integrate Service From Github
-----------------------------


1. redmine

	Enable WS for repository management
	Api Key

	```
Started GET "/sys/fetch_changesets?key=66hRNJmN9lxccnpfXsZ6&id=vimconfig" for 127.0.0.1 at 2014-02-18 15:19:37 +0800
Processing by SysController#fetch_changesets as */*
  Parameters: {"key"=>"66hRNJmN9lxccnpfXsZ6", "id"=>"vimconfig"}
  Rendered text template (0.0ms)

==> log/git_hosting.log <==
2014-02-18 15:19:37 +0800 INFO [GitHosting] ["Executing RESYNC_ALL operation on Gitolite configuration"]
2014-02-18 15:19:37 +0800 INFO [GitHosting] ["Installing hook 'redmine_gitolite' => 'post-receive.redmine_gitolite.rb'"]
2014-02-18 15:19:37 +0800 INFO [GitHosting] ["Hook destination path : '~/.gitolite/hooks/common/post-receive'"]
2014-02-18 15:19:37 +0800 INFO [GitHosting] ["Our 'redmine_gitolite' hook is already installed"]
2014-02-18 15:19:37 +0800 INFO [GitHosting] ["Global directory 'post-receive.d' is already present, will not touch it !"]
2014-02-18 15:19:37 +0800 INFO [GitHosting] ["Installing hook 'mail_notifications' => 'post-receive.mail_notifications.sh'"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Hook destination path : '~/.gitolite/hooks/common/post-receive.d/mail_notifications'"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Our 'mail_notifications' hook is already installed"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Updating key directory for projects : 'gk-source, testing, testing-uat, vimConfig'"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Using existing Gitolite repository : 'repositories/gk-source.git' for update"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Using existing Gitolite repository : 'repositories/testing.git' for update"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Using existing Gitolite repository : 'repositories/testing-uat.git' for update"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Using existing Gitolite repository : 'repositories/vimconfig.git' for update"]
2014-02-18 15:19:38 +0800 WARN [GitHosting] ["Committing corrections to Gitolite Admin repository"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Updating Hook URL: http://git.xlaa.tk/githooks/post-receive"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Updating Debug Hook: true"]
2014-02-18 15:19:38 +0800 INFO [GitHosting] ["Updating Hooks Are Asynchronous: false"]

==> log/production.log <==
Completed 200 OK in 1530.4ms (Views: 0.5ms | ActiveRecord: 0.0ms)

	```
