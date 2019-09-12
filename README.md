### Don't use it!
### This library is not complate!
### 不要使用这个库，这只是一个应急作品，由于应用的项目已部署到客户的生产环境无法撤回，所以被迫保留。有已知BUG并且我不会再花时间更新它。
Yii2 cronjobs extension
========
Easiest way to put crontab on your console scripts.

This extension is based on [this](https://github.com/DenisOgr/yii2-cronjobs).
Thanks [Denis Porplenko](https://github.com/DenisOgr).

But with a few changes:
- support php 7.*


Installation
------------

- **Step 1:** The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist willcn/yii2-cronjobs "dev-master"
```

or add

```
"willcn/yii2-cronjobs": "dev-master"
```

to the require section of your `composer.json` file.
- **Step 2:** Set aliase  @runnerScript in console config. This absolutely path to runner script (I can not find another way to get runner script).
Change path to runner script as your project (For Yii2 Basic application). 
```
Yii::setAlias('@runnerScript', dirname(__DIR__) .'/yii');
```

- **Step 3:** Add to console config:
```
'controllerMap' => [
       'cron' => [
           'class' => 'willcn\cronjobs\CronController'
       ],
   ],
```
- **Step 4:**  Add task to system scheduler (cron on unix, task scheduler on windows) to run every minute:

```sh
* * * * * /path/to/yii/application/protected/yiic cron
```
Usage
-----

Add in params array with cron sets:
```
'cronJobs' =>[
        'test/example1' => [
            'cron'      => '* * * * *',            
        ],
	'test/example2' => [
            'cron'      => '10 * * * *',            
        ],

    ],
```

You can point any settings from [this](https://github.com/Yiivgeny/Yii-PHPDocCrontab/blob/master/examples/ExampleRuCommand.php).


