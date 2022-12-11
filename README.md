# Lern-Bericht M183 XSS
### von Janic Holzherr

## Einleitung

In diesem Lernbericht erkläre ich Cross-Site-Scripting (XSS) und wie man sich dafür schützen kann. XSS ist eine Art von Cyberangriff, bei dem Angreifer bösartigen Code in die Webseiten anderer Benutzer einschleusen, um deren Browser dazu zu bringen, schädliche Aktionen auszuführen.

## Was habe ich gelernt?

Ich habe verschiedene Methoden gelernt wie man sich als Developer vor einer XSS Attacke schützen kann. Dazu gehört alle Eingaben welche der Benutzer machen kann müssen zuerst überprüft werden ob sie code enthalten oder nicht. Weiter unten in diesem Lernbericht zeige ich eine Möglichkeit sich vor XSS Attacken zu schützen.

## Beschreibung

```Java
// Eine Methode, die Benutzerdaten validiert und bereinigt (Formatvalidator)
public String sanitizeUserInput(String userInput) {
  // Entferne mögliche schädliche Skripts oder HTML-Code aus der Eingabe des Benutzers
  String sanitizedInput = userInput.replaceAll("<script>", "")
                                   .replaceAll("</script>", "")
                                   .replaceAll("<style>", "")
                                   .replaceAll("</style>", "")
                                   .replaceAll("<", "&lt;")
                                   .replaceAll(">", "&gt;");

  // Rufe die encode-Methode auf, um sicherzustellen, dass alle Zeichen, die in URLs verwendet werden können, korrekt codiert werden
  sanitizedInput = URLEncoder.encode(sanitizedInput, "UTF-8");

  return sanitizedInput;
}
```
Das scheint auf den ersten Blick etwas unhandlich, löst aber das Problem. Mit dieser Methode kann man nun jeden Userinput "reinigen", das bedeutet man nimmt alle "verbotenen" Zeichen aus dem Input heraus.

Eine andere Möglichkeit, sich vor XSS-Attacken (Cross-Site Scripting) zu schützen, ist das Validieren von Benutzereingaben. Auf diese Weise werden unerwünschte Skripte und HTML-Code von Benutzern verhindert, bevor sie in die Website eingefügt werden. Um Benutzereingaben bezüglich XSS (Cross-Site Scripting) zu validieren, kann man ähnliche Methoden wie bei der allgemeinen Validierung von Benutzereingaben verwenden. Eine Möglichkeit ist die Verwendung von Regular Expressions (RegEx), um sicherzustellen, dass keine unerwünschten Skripte oder HTML-Code in die Eingaben eingegeben werden.Eine andere Möglichkeit ist die Verwendung von Formatvalidatoren (Codebeispiel), die festlegen, welche Zeichen und Zeichenfolgen in einem bestimmten Eingabefeld erlaubt sind. Es ist wichtig, mehrere Schichten von Validierung zu verwenden, um sicherzustellen, dass Benutzereingaben sicher und frei von XSS-Attacken sind.

![XSS Basics](https://media.geeksforgeeks.org/wp-content/uploads/20190516152959/Cross-Site-ScriptingXSS.png)

## Verifikation

In meinen Medien die ich vorgestellt habe, sieht man verschiedene Möglichkeiten sich vor XSS zu schützen, und genau das habe ich gelernt in diesem Modul. 

# Reflektion zum Arbeitsprozess

Im Modul 183 habe ich gemerkt, das ich mich weniger lange konzentrieren konnte als im Modul zuvor. Das ist etwas was ich im nächsten Modul ändern möchte, da es meine produktivität verschlechtert.

Was hingegen gut gelaufen ist, war das ich mich darauf fokussiert habe die Aufträge zu lösen und bei eventuellen Fehlermeldungen habe ich mir immer meinen Code durchgelesen um das Problem wirklich zu verstehen. Dadurch habe ich gelernt wie man richtig Debuggt.

Im nächsten Modul möchte ich versuchen meine Arbeit immer in Arbeitspakete einzuteilen. Dadurch kann ich meine Konzentration fördern und mir klare Ziele vorstellen welche ich während des Morgens erreichen möchte.
