### teamviewer installation. Inspired from [Official Help](http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#other)

- Add i386 architecture
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo dpkg --add-architecture i386
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo apt-get update
    </code></pre>

- Download teamview deb
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ wget http://downloadeu2.teamviewer.com/download/teamviewer_linux.deb
    </code></pre>

- Install the dependency by `apt-get`
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo apt-get install -f
    </code></pre>

- Install teamviewer by `dpkg`
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo dpkg -i teamviewer_linux.deb
    </code></pre>
