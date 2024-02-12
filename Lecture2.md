* 12:25 - vi diskuterer valg af framework
* 12:30 - Ruby with sinatra babyyyy
* 12:39 - `gem install bundler` til dependency mangament
  * `bundle init` til at lave gem file
  * Tilføjer puma til gemfile -> `bundle add puma`
  * Laver en test index (myapp.rb) fil til Sinatra
  * kør test fil `bundle exec ruby myapp.rb` -> Den fejler fordi den mangler rackup
	 `bundle add rackup`
* 12:46 - Vi blev enige om at bruge den ruby version der ligger i apt som standard (3.0.2)
	  For at enforce det her laves en .ruby-version fil, med indhold 3.3.0
* 12:58 - Der er nogle problemer med at installerer gems på visse maskiner (FilePermissionError)
* 13:02 - Vi kommer uden om problemer ved at installere "rbenv" igennem homebrew
* 13:09 - Vi havde nogle problemer med rbenv, fordi /usr/local/share ikke var ejet af brugeren.
  * `chown -R <user> /usr/local/share` fixede dette
* 13:12 - Vi vælger at bruge 3.3.0 i stedet da vi alligevel alle sammen bruger rbenv (`rbenv install 3.3.0`)
* 13:15 - Vi installerer Homebrew til Linux (linuxbrew) for at kunne installere rbenv og ruby-build.
* 13:15 - Sætter ruby 3.3.0 som standard version (`rbenv global 3.3.0`)
* 13:20 - rbenv skal init når terminalen startes
  * tilføjes til .zshrc `eval “$(rbenv init -)”`
* 13:30 - De nye test er grønne for nogen, men ikke andre
  * Kopier database til forventet sti `cp minitwit.db /tmp/minitwit.db`
* 13:30 - Linuxbrew tager ekstremt lang tid om at installere, men bliver færdig. Alle linuxbrew operationer tager dog meget lang tid.
* 13:40 - Et gruppemedlem har oplevet lignende problemer tidligere og oplevede at root cause var prolemer med WSL's DNS-lookup. Dette fikses ved at indsætte "[networking] generateResolvConf = false" i "/etc/wsl.conf". Herefter slettes "/etc/resolv.conf" og en ny tilføjes med indholdet "nameserver 8.8.8.8" eller lignende DNS-server, og denne fil gøres immutable med "sudo chattr +i resolv.conf". Dette tvinger WSL til at bruge en bestemt nameserver og efter dette fikses netværk-hastighed.

* 13:50 - Vi installerer dependencies så sinatra kan tale med db
  * `bundle add activerecord`
  * `bundle add sinatra-activerecord`
  * `bundle add rake`


