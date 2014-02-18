webhooks
--------


1. in repo settings: "Webhooks & Services" 

	"add webhooks": http://domain/github_hook?project_id=vimconfig

2. in redmine repo

	su git
	git clone --mirror git@github.com:git_user/project.git
	cd project.git
	git fetch -q --all


Integrate Service From Github
-----------------------------


1. redmine

	Enable WS for repository management
	Api Key
