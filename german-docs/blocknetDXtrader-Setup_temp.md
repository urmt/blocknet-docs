# BLOCKNET
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/block.PNG "Logo Title Text 1")

Das Internet der Blockchains

## Blocknet Dezentralisierte Börse Setup-Anweisungen für Handelnde

**Diese Anweisungen erklären das Handeln auf der dezentralisierten Börse von Blocknet** 

* Blocknets DX nutzt die XBridgep2p™-Routertechnologie um es Nutzern zu ermöglichen, Tokens und Assets auszutauschen, und ebenso "smart-contracts" über verschiedenen Blockchains hinweg bereitzustellen.

## Übersicht
Das Setup erfordert eine Verknüpfung der Blocknet Wallet mit all jenen Coin-Wallets, die man handeln möchte. Zu diesem Zeitpunkt gibt es hierfür keine Automatisierung, man benutzt hierfür einfach die aktuellste Blocknet Wallet bis die GUI (grafisches User-Interface) finalisiert ist. Die Konfiguration bedarf der händischen Erstellung und/oder Editierung der .conf-Dateien: 

 * xbridge.conf

 * Konfigurationsdatei jeder Währung, die getraded werden soll

Die Verknüpfung geschieht über die RPC-APIs der jeweiligen Wallets. Aus Sicherheitsgründen wird empfohlen, alle Wallets auf einem System laufen zu lassen, sowie über die IP-Adresse des localhost (127.0.0.1) zu verbinden, auch wenn es generell möglich ist, die Wallets auf unterschiedlichen Systemen zu hosten und über deren IP zu verbinden. Eine grundlegende Dokumentation rund um die JSON-RPC-Schnittstelle kann man @ https://en.bitcoin.it/wiki/Running_Bitcoin.


## Blocknet DX Börse Tutorial Video
 * [DX Börse Tutorial](https://www.youtube.com/watch?v=DlYbDzG_l5w)


## Anforderungen

* Die aktuellste Version des Blocknet Clients muss installiert, verschlüsselt und voll synchronisiert sein. [GitHub Releases](https://github.com/BlocknetDX/BlockDX/releases)

* Die aktuellste Wallet jeder Währung, die getraded werden soll, ebenso voll synchronisiert und verschlüsselt

     * Die Währung, die gehandelt werden soll, sollte nun auf eine eindeutig benannte Adresse dieser Wallet gesendet werden 

* Richtig konfigurierte .conf-Dateien für jede Wallet

---

## Setup  .conf-Dateien der zu tradenden Wallets
Jede Wallet all jener Coins, die man traden möchte, muss mit einem Nutzernamen und Passwort versehen werden und "eine" IP erlauben, als Beispiel wenn man alles auf dem lokalen Rechner installiert hat, ist die IP:127.0.0.1

 * Eine vollständige Liste der Konfigurationen kompatibler Wallets findet man hier: [Wallet Konfigurationen](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md)

 * Lade und installiere die aktuellste Wallet, lass sie voll synchronisieren, schließe dann die Wallet

 * Klicke den Start-Button (Windows-Icon) auf dem Desktop, und schreibe in das Feld “Search program and files” den Begriff “%appdata%”, der “Roaming”-Ordner sollte nun angeboten werden. Klicke auf “Roaming” oder drücke Return/Enter.

 * Lokalisiere den jeweilige Daten-Ordner der gewünschten Währung, als Beispiel: Bitcoin

 * Sollte in diesem Ordner keine .conf-Datei sein, musst du diese mit zB. Notepad erstellen.

 * Öffne [Wallet Konfigurationen](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md) und kopiere die Konfigurationsinformationen der gewünschten Wallet in die erstellte oder bestehende conf-Datei. (dies kann in der conf-Datei einfach hinzugefügt werden zu den Informationen, die diese gegebenenfalls schon beinhaltet):
   * Beispiel: bitcoin.conf
   
   ```
   server=1
   listen=1
   rpcuser=yourusername
   rpcpassword=yourpassword
   rpcallowip=127.0.0.1
   ```
   
   * Gehe sicher, daß die Konfiguration korrekt ist. Sei dir im Klaren, dass nicht jede Währung/Wallet die gleiche Konfiguration hat.

 * Ändere `rpcuser` und `rpcpassword` nach deinen eigenen Wünschen. Aus Sicherheitsgründen solltest du für unterschiedliche einzigartige Nutzernamen und Passwörter für jede Wallet haben

 * Wenn du einen einzigen Rechner benutzt nutze die IP: `127.0.0.1`

 * Wenn alles fertig eingegeben ist, drücke Datei, speichern als, und schreibe `bitcoin.conf` hinein.
    * Versichere dich, dass die Datei nicht `bitcoin.conf.txt` ist

 * Speichere die Datei und sichere sie dann in dem entsprechenden Ordner der Wallet
    * In diesem Beispiel: %Appdata%/Roaming/Bitcoin 

 * Nicht vergessen, den Nutzername, das Passwort und die IP zu merken

 * Erstelle entsprechende .conf-Dateien für jede Wallet, deren Währung du auf der DEX handeln möchtest.
    * Versichere dich, dass `rpcuser` und `rpcpassword` aus Sicherheitsgründen für jede zu tradende Währung unterschiedlich sind
 
---

## Konfiguration für die Coin-Adressen
Erstelle in jeder Wallet eine neue Adresse und benenne sie (label) sie mit einem für dich eindeutigen spezifischen Namen, als Beispiel "DX address" (XBridge erwartet eine Adresse mit Label!!)

 * Um eine neue Adresse zu erstellen, gehe im Programm auf den “receive”-Tab und klicke auf “new address”

 * Um eine Adresse mit einem Namen/Label zu versehen, klicke mit der rechten Maustaste auf die Adresse und klicke auf das “label”-Feld.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/labelledaddress.PNG "Logo Title Text 1") 

 * Sende anschließend die gewünschte Anzahl an Coins an diese Label-Adresse
 
 * Dies musst du in allen Wallets machen, die du für die DEX handelbar machen möchtest
 
---

## Konfiguration xbridge.conf

Die XBridge-Technologie von Blocknet ist in der aktuellen Version integriert. Siehe hier [GitHub](https://github.com/BlocknetDX/BlockDX) für den Programm-Code.

 * Um die komplette Liste der .conf-Dateien einzusehen, gehe zu: [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md).

 * Erstelle/editiere die Datei `xbridge.conf` und speichere sie in das Datenverzeichnis von Blocknet, als Beispiel findest du dieses unter Windows hier: C:\Users\[yourusername]\AppData\Roaming\blocknetdx\

 * Anmerkung: um einen Crash oder Fehltrades zu vermeiden, editiere die Datei `xbridge.conf` nur mit den Werten, die du auch handeln möchtest.

 * Füge den RPC Nutzernamen und das entsprechende Passwort für jede gewünschte Währung in die Felder “Username” und “Password”.
 
 * Füge den Namen der entsprechenden Adresse und jeder gewünschten Währung, die du selbst benannt hast, in das Feld "labelled receive address"
 
 * Versichere dich, dass der Rest der Konfiguration den Einträgen für jeden Coin verglichen mit der Datei [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md) entspricht

 * Speichere die Datei (solltest du sie nur editiert habe, drücke einfach auf speichern, wenn du sie neu erstellt hast, drücke "speichern als" und sichere sie unter den Namen: `xbridge.conf`
    * Versichere dich, dass die Datei nicht `xbridge.conf.txt` heisst danach.

 * Speichere diese Datein in das Datenverzeichnis von Blocknet, als Beispiel für Windows: "C:\Users\[yourusername]\AppData\Roaming\blocknetdx\"

 * Du wirst in Zukunft von Zeit zu Zeit diese Datei wieder editieren, wenn du neue Coins hinzufügen willst, oder Änderungen vornehmen möchtest an `RPCusername` `RPCpassword` `Port` `Address` 
 
 * Ändere keine anderen Einträge in diese Datei, außer du bist im Testnet und leitest Testprozeduren.
 
---

## Ablauf Starten
 * Starte als erstes alle Wallets der Coins, die du auf deiner Service-Node unterstützt
    * Versichere dich, daß jede Wallet voll synchronisiert und ungesperrt ist.

 * Starte die Blocknet Wallet nachdem du alle anderen gewünschten Wallets gestartet hast.
     
---

## Überprüfe die Kommunikation zwischen den Wallets.
Um sicherzugehen, dass der XBridge Client mit den wallets und den -conf-Dateien richtig kommuniziert, navigiere in das Daten-Verzeichnis von Blocknet (Windows): C:\Users\yourusername\AppData\Roaming\blocknetdx\

   * Öffne den "log"-Ordner. Öffne nun die Log-Datei mit dem aktuellsten Datum/Zeitstempel. Als Beispiel: `xbridgep2p_20170831T181856.log`
   * Jede Log-Datei wird solange aktualisiert bis der Core-UI geschlossen wird. Wenn der Core-UI neu gestartet wird, wird ein neue Log-Datei angelegt.

Wenn du den Core-UI startest, wirst du die Initialisierung sehen mit den Werten aus der Datei `xbridge.conf`, die du erstellt hast:

![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/dxstart.PNG "Logo Title Text 1") 

 * Warte nun, bis du Einträge des Typs “HTTP: resp 200” erhälst. Dies zeigt an, daß die Wallets über RPC miteinander kommunizieren und die Einstellungen erfolgreich waren. Versichere dich, dass jede unterstützte Wallet einen Eintrag “HTTP: resp 200” und den passenden Adressnamen (Label) hat.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/resp_200.PNG "Logo Title Text 1") 

 * Anmerkung: Wenn du inmitten der “HTTP: resp 200” Nachrichten  einen Eintrag ähnlich des nachfolgenden siehst, `[I] 2017-Apr-19 17:48:31 [0x2],listaccounts exception couldn't connect to server`, bedeutet dies, das zumindest einer der verknüpften Wallets nicht ordnungsgemäß läuft.

 * Anmerkung: Wenn du nicht den Eintrag “HTTP: resp 200” erhältst, ist zu überprüfen, ob der/die Ports, die in der conf.-Datei angegeben wurden, mit denen übereinstimmen, die für die jeweilige Wallet vorgegeben wurden. Um dies zu überprüfen, öffne die Windows-Kommandozeile und schreibe `netstat -an` hinein, und überprüfe dann, welche Ports über den localhost (127.0.0.1), oder manchmal über (0.0.0.0), genutzt werden.

--- 
 
## Place an Order
Once you’ve confirmed that the wallets are communicating and setup has been successful, do the following:

* In the “BlocknetDX” tab of the Blocknet wallet, click on the “New Transaction” button. A new window will open:
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/newTX.PNG "Logo Title Text 1")   

* Click on the “Address book” icon. This opens up a new window that displays the addresses you created in each currency pair wallet.
   
   ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/address_book.PNG "Logo Title Text 1")   

  * Notes: 
  
    * If you do not see these addresses, it means that your wallets are not communicating over RPC
    
    * It may take up to about 30 seconds for xbridge to connect with your wallets, but once startup has completed it will populate your currency pair addresses

    * Do not manually paste an address into the “from” and “to” fields. Select addresses that xbridge has been given by your currency pair wallets.
      
* On the "from" and "to" sides, click the "Address Book" and double-click the currency's you want to trade
    
* Your address and account balance will populate for each currency
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/btc_dyn_newtx.PNG "Logo Title Text 1")
    
   * In this example we are trading Bitcoin for Dynamic
   
* Choose the amount you wish to trade for and click "New Transaction"
   
* The new TX will then be posted to the Blocknet DX for someone to accept.
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/btc_dyn_posted.PNG "Logo Title Text 1")
    
   * In this example TX we are trading 0.0006 BTC for 1 DYN
   
* To accept a trade, side click the posted TX and click accept

* To cancel your TX post, side click your TX and click cancel

---

## Problem Diagnosis
* To verify that each wallet is communicating with xbridge make sure the created receive addresses for each wallet is listed in the address book. If this part fails, close your wallets and review their configuration files.

* Ensure you have sent the funds you wish to trade with to the labelled address. Ensure these are confirmed.

* If you made changes to any .conf file you need to close and restart that wallet, including Blocknet 

* Verify the ports are actually open. You may use Command Prompt to do so by typing in `netstat -an` and reviewing the print. Check that the ports you specified in the .conf files (ex: 8332 for Bitcoin) are open over localhost (127.0.0.1).

* Ensure all .conf files are configured properly. These configurations are very case-sensitive. Any wrong data entered in them could be causing the issues.

* Check that no OS-based firewall is blocking communication. You may do this through your firewall’s interface.

* Check the xbridge log for any errors in: C:\Users\yourusername\AppData\Roaming\blocknetdx\log

* Check on general wallet events in C:\Users\yourusername\AppData\Roaming\walletname\debug.log

---

## Security Tips
(With thanks to threepwood)

Since our technology essentially makes you your own exchange, here are some tips on how to keep your money safe.

   * The Blocknet’s team will never ask for your private keys or coins. Do not get fooled by impersonators.
Exchanges

   * Always move your coins from exchange to your private wallet.

   * Use long and random password.

   * Set up 2FA on logins and any withdrawals.

   * Disable password recovery via SMS/phone service. Disable all password recovery options for maximum security.

   * Recovery passwords are fine but keep them printed and offline.

   * Make sure your stored emails do not contain any extra information such as passwords or social security numbers.

   * Use different email addresses where possible. This limits the ability for hackers to run their automated "Forgot my password" links. 
   
   * Online Activity / Personal Information Disclosure. Do not promote your coin count etc online.

   * Limit your online public persona. This can attract unwanted attention which can make you a target.

   * Disable any online accounts you no longer use.

   * Assume hacking groups are building up social profiles on yourself. Your interests, time you are usually online, who you interact with.

   * Hacking groups use automated scripts so if those resources are exhausted they will try to social engineer your contacts.

   * Hacking groups are experts at social engineering. They have done this thousands of times.

   * Do not open random links and files provided in Slack, etc.

   * Do not fall for sob stories (Boohoo I lost all my coins) without proper due diligence.

   * Take multiple backups of your private keys regularly.

   * Verify backup by importing keys to the client.

   * Store your backups in M-DISC or in paper format.

   * Use dedicated wallet / staking PC and make it your safe haven. DO NOT USE IT FOR ANY OTHER ONLINE ACTIVITIES.

   * Encrypt your hard drives.

   * Use open source where possible.

   * Keep your software updated.

   * Do not install software from unknown 3rd party actors.

   * Use network level segmentation and mitigate attack surface against your wallet PC.