---
layout: post
title:  "Setting up SonarQube for swift on Mac OSX"
date:   2017-11-01 10:00:00
categories: Illustration
tags: SonarCube Swift CodeCoverage
---

### Step 1. Download and setup `SonarCube`

* [Download SonarQube](https://www.sonarqube.org/downloads/)
* Unzip downloaded file. 
* Move downloaded file under `/Applications/` folder. (I prefer it to keep it that way)
* Rename it to `SonarQube` and delete version suffix.

---

### Step 2. Downloading and setting up `Sonar Scanner`

* [Open download SonarScanner page](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) and click on `Mac OS X 64 bit` to download Mac OS X specific `SonarScanner`
* Unzip downloaded file. 
* Move downloaded file under `/Applications/` folder. (I prefer it to keep it that way)
* Rename it to `SonarScanner` and delete version suffix.

---

### Step 3. Updating `.bash_profile` with new `PATH`

Start `Terminal` and run following command.

```
cd ~/
vi .bash_profile
```

* Above commands will open your `bas_profile` in `vi` editor.
* Use down-arrow key to jump to last line.
* Use left-right arrows to navigate to last character.
* Press `i` to enable insert mode.
* Copy & paste following lines.

```
export PATH=$PATH:/Applications/SonarScanner/bin
export PATH=$PATH:/Applications/SonarQube/bin
```

* Press `esc` key and `:` will appear at bottom-left corner in `vi` editor.
* Enter `wq` to save & quit.

---

### Step 4. Setting up `SonarSwift` from `Backelite`.

* [Open downloads page](https://github.com/Backelite/sonar-swift/releases)
* Download jar. In my case, I downloaded `backelite-sonar-swift-plugin-0.3.5.jar`
* Move this jar file under following folder.

```
/Applications/SonarQube/extensions/plugins/
```

---

### Step 5. Starting up `SonarQube`.

Run following command to start `SonarQube` server.

```
sh /Applications/SonarQube/bin/macosx-universal-64/sonar.sh console
```

You should see console as follows if everything goes well.

```
Running SonarQube...
wrapper  | --> Wrapper Started as Console
wrapper  | Launching a JVM...
jvm 1    | Wrapper (Version 3.2.3) http://wrapper.tanukisoftware.org
jvm 1    |   Copyright 1999-2006 Tanuki Software, Inc.  All Rights Reserved.
jvm 1    | 
jvm 1    | 2017.11.02 16:23:18 INFO  app[][o.s.a.AppFileSystem] Cleaning or creating temp directory /Applications/SonarQube/temp
jvm 1    | 2017.11.02 16:23:18 INFO  app[][o.s.a.es.EsSettings] Elasticsearch listening on /127.0.0.1:9001
jvm 1    | 2017.11.02 16:23:18 INFO  app[][o.s.a.p.ProcessLauncherImpl] Launch process[[key='es', ipcIndex=1, logFilenamePrefix=es]] from [/Applications/SonarQube/elasticsearch]: /Applications/SonarQube/elasticsearch/bin/elasticsearch -Epath.conf=/Applications/SonarQube/temp/conf/es
jvm 1    | 2017.11.02 16:23:18 INFO  app[][o.s.a.SchedulerImpl] Waiting for Elasticsearch to be up and running
jvm 1    | 2017.11.02 16:23:18 INFO  app[][o.e.p.PluginsService] no modules loaded
jvm 1    | 2017.11.02 16:23:18 INFO  app[][o.e.p.PluginsService] loaded plugin [org.elasticsearch.transport.Netty4Plugin]
```

But once you see following message under console, you should start brownser.

```
jvm 1    | 2017.11.02 16:23:40 INFO  app[][o.s.a.SchedulerImpl] Process[ce] is up
jvm 1    | 2017.11.02 16:23:40 INFO  app[][o.s.a.SchedulerImpl] SonarQube is up
```

---

### Step 6. Logging in

Go to browser. Open following URL.

```
http://localhost:9000/about
```

* Click on Log in
* Use `admin` as username, `admin` as password.

---

### Step 7. Setting `SwiftLint` as default profile for `Swift`

Open following URL.

```
http://localhost:9000/profiles
```

![Set SwiftLint as Default](https://github.com/Backelite/sonar-swift/raw/develop/SwitchProfiles.png)

Scroll down to `Swift` section.

Set `SwiftLint` as default profile.

---

### Step 8. Setting up the project

Navigate to following URL.

```
http://localhost:9000/admin/projects_management
```

* Click on `Create Project`.
* Enter Project name
* Enter project key
* Click `Create`

### Step 9. Performing Analysis on your project.

* Start `Terminal`
* Navigate to your project's root directory where you've your `project.xcodeProject` file.

For Example,

```
cd ~/Projects/iOSApplications/myProject
```

To Start analysis, run following command.

```
sonar-scanner -Dsonar.projectKey=MyProjectKey -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000
```

NOTE: Make sure you replace `MyProjectKey` with your project key.

Analysis will begin with following console log.

```
INFO: Scanner configuration file: /Applications/SonarScanner/conf/sonar-scanner.properties
INFO: Project root configuration file: NONE
INFO: SonarQube Scanner 3.0.3.778
INFO: Java 1.8.0_121 Oracle Corporation (64-bit)
INFO: Mac OS X 10.12.6 x86_64
INFO: User cache: /Users/e070190/.sonar/cache
INFO: Publish mode
INFO: Load global settings
INFO: Load global settings (done) | time=56ms
```

And, analysis will end with following console log.

```
INFO: Task total time: 21.407 s
INFO: ------------------------------------------------------------------------
INFO: EXECUTION SUCCESS
INFO: ------------------------------------------------------------------------
INFO: Total time: 22.791s
INFO: Final Memory: 57M/1531M
INFO: ------------------------------------------------------------------------
```

### Step 10. Viewing the reports.

Navigate to following URL.

```
http://localhost:9000/dashboard?id=MyProjectKey
```

NOTE: Make sure you replace `MyProjectKey` with your project key.

![Sample Report](https://github.com/Backelite/sonar-swift/raw/develop/screenshot.png)