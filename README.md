vim
===

### vimConfig quick start

```
git clone https://github.com/gankkank/vimConfig
cd vimConfig

#use basic version without trouble
git checkout tags/v1.0
cp -r .vim* ~/

#use advance version with AutoClose
git checkout tags/v1.1
cp -r .vim* ~/

```

### git repos used

** no .git/ should exist in subdirectories when commit **

* for hightlight

	git clone git://github.com/kchmck/vim-coffee-script.git

	git clone git://github.com/tpope/vim-markdown.git

	git clone git://github.com/vim-ruby/vim-ruby.git

	git clone git://github.com/pangloss/vim-javascript.git


* for usability

        git clone git://github.com/vim-scripts/bash-support.vim.git

        git clone git://github.com/vim-scripts/AutoClose.git

	\#git clone git://github.com/jiangmiao/auto-pairs.git


* main for ref

	https://github.com/vim-scripts


### ref notes

* bash-support ``vi xxx.sh``

  template: ~/.vim/bundle/bash-support/bash-support/templates/Templates

  press "" or '' to surround a WORD

  insert user function: \sfu

  comment user function, range: \cfu, \cfr

  commend with keyword BUG, TODO, TRICKY, WARNING;  \ckb, \ckt, \ckr, \ckw

  Run: check syntax,executable, set args, run; \rc, \re, \ra, \rr 

  
* auto close ``[, (, {, ", '``

  press ) to move the cursor outside the parens. such as when: echo "hello|"
