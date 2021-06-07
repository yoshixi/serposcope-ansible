# 起動方法

ssh を使用せず、local で直接起動することができます。

```
$ cd ansible
$ ansible-playbook -i localhost, -c local site.yml
```

# 作業メモ

## apt で java 8 を install できない

- amazon が提供している JDK を使う

[ディスカッションリンク](https://www.reddit.com/r/Ubuntu/comments/beqbs2/webupd8_oracle_java_jdk_8_installer_ppa/)
[Amazon's OpenJDK8-based Coretto HOME](https://docs.aws.amazon.com/corretto/latest/corretto-8-ug/generic-linux-install.html)

## `service serposcope start` 環境変数 JAVA_HOME のエラーで動かない

[systemctl の環境変数を設定する](https://stackoverflow.com/questions/56100690/how-to-configure-java-home-with-openjdk)

こんな感じ

```yml
- name: Copy nginx configuration for WordPress
  template: src=systemctl-override.conf dest=/etc/systemd/system/serposcope.service.d/override.conf
```

## Port が 7134 しか開かない

Nginx で動く
[無料の GRC 代替クラウドサービス「Serposcope」を ConoHa で動かす](https://qiita.com/moroi/items/c6c6336f125f33b1aca4)

## そのほか

- アクセスができない
  - 7134 を解放する
