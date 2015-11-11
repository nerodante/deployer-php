# Release the php project  with Deployer



### 1. [installation](http://deployer.org/docs/getting-started)

### 2. Config

``` php
<?php
require 'recipe/common.php';
// 设置server，stage信息
server('prod', '10.211.55.7', 22)
    ->user('root')
    ->password('123qwe')
    ->stage('production')
    ->env('deploy_path', '/root/www');

server('dev', 'your server ip', 22)
    ->user('ssh_username')
    ->password('ssh_password')
    ->stage('dev')
    ->env('deploy_path', '/root/www');
// 设置版本仓库，从这里down代码传至server
set('repository', 'your repository here');
set('keep_releases', 3);
// 部署的流程有先后顺序，否则会报错
task('deploy', [
    'deploy:prepare',
    'deploy:release',
    'deploy:update_code',
    'deploy:symlink'
])->desc('Deploy your project');
```

### 3. run deploy command

* dev (task-name) (stage)

``` shell
dev deploy production
```

### 4. rollback



### 参考资料

* [Deployer Docs](http://deployer.org/docs)