查看目录大小  `du -sh Runtime/` 结果:`360M Runtime/`

查看已安装的shell `cat /etc/shells`
切换shell `chsh -s /bin/bash`
创建软连接 `ln -s source_file target_file`

Mac连接充电提示音
开启：`defaults write com.apple.PowerChime ChimeOnAllHardware -bool true; open /System/Library/CoreServices/PowerChime.app`
关闭：`defaults write com.apple.PowerChime ChimeOnAllHardware -bool false; killall PowerChime`


Python版本管理工具`pyenv`
> 安装 `brew install pyenv`
> 查看已安装的Python版本 `pyenv versions`星号表示当前激活的Python版本
> 只查看当前激活的Python版本 `pyenv version`
> 查看可安装的Python版本 `pyenv install --list`
> 安装新的Python `pyenv install 3.4.3`
> 卸载Python版本 `pyenv uninstall`
> 设置全局的Python版本 `pyenv golbal 3.4.3`
> 设置本地的Python版本 `pyenv local 3.4.3` 本地版本的优先级高于全局版本
> 设置面向shell的Python版本 `pyenv shell 3.4.3` shell版本的优先级高于本地版本
> 如果无法切换python，在shell理执行`if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi`
> 配置pyenv
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
$ echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
$ exec $SHELL

sphinx的安装与使用
> 安装 `sudo easy_install sphinx`
> 安装主题 `pip install sphinx_rtd_theme`
> 初始化项目 `sphinx-quickstart`
> 更换主题 修改conf.py文件html_theme = '主题名称'
