### thin
---
http://code.macournoyer.com/thin/

https://github.com/macournoyer/thin

```
gem install thin
gem 'thin'
thin start
gem 'faye-websocket'
gem 'thin'

thin -R config.ru -a 127.0.0.1 -p 8080 start
thin -p 9292 -P tmp/pids/thin.pid -l logs/thin.log -d start
```

```ruby
# config/initializers/thin_action_cable.rb
Rails.application.config.action_cable.use_faye = true
Faye::WebSocket.load_adapter 'thin'

```yml
# thin config -C config/thin.yml
---
user: www-data
group: www-data
pid: tmp/pids/thin.pid
timeout: 30
wait: 30
log: log/thin.log
max_conns: 1024
require: []
environment: production
max_persistent_conns: 512
servers: 1
threaded: true
no-epoll: true
daemonize: true
socket: tmp/sockets/thin.sock
chdir: /path/to/your/apps/root
tag: a-name-to-show-up-in-ps aux
```
```


