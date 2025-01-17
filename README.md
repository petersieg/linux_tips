# linux_tips
some tips on using linux

To list all packages intentionally installed (not as dependencies) by apt commands, run the following :
'''
(zcat $(ls -tr /var/log/apt/history.log*.gz); cat /var/log/apt/history.log) 2>/dev/null |
  egrep '^(Start-Date:|Commandline:)' |
  grep -v aptdaemon |
  egrep '^Commandline:'
'''
