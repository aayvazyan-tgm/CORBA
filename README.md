CORBA
=====

A CORBA implementation between two different Languages.

Um das python script auf debian zum laufen zu bekommen müssen folgende schritte durchgeführt werden:

Python-all-dev installieren
omniORB und omniORBpy konfigurieren & installieren.
Interface in IDL Spezifizieren
interface Echo {
string echoString(in string mesg);
};
In echo.idl speichern
Die IDL wird für c++ compiliert:
omniidl -bcxx echo.idl
Das selbe geschieht für python mit 
omniidl -bpython echo.idl
Und nun wird auch noch die example_echo.idl:
module Example {
  interface Echo {
    string echoString(in string mesg);
  };
};
Für python kompilliert
omniidl -bpython example_echo.idl
In /etc/omniORB.conf muss folgende zeile angepasst werden:
InitRef = NameService = corbaname::localhost

Nun lässt sich mittels python main.py das pythonscript starten:
Das Script lässt sich unter folgendem repository finden:
https://github.com/aayvazyan-tgm/CORBA
