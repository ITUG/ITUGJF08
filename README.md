# ITUG JourFixe #08
## Vis-à-vis: Zweisprachige Editionen mit TUSTEP (Urs Leo Gantenbein)

## Beschreibung
### Aufgabenstellung  
Zwei Texte sollen auf gegenüberliegenden Seiten mit #SATZ gesetzt werden, zum Beispiel ein lateinischer Text **seneca1.tf** und seine deutsche Übersetzung **seneca2.tf**:  

![vav1](https://user-images.githubusercontent.com/101052082/159179569-1f17e815-365e-40bb-b6bf-1be1590fe4ae.jpg)

Die gegenüberliegenden Seiten sollen sich dabei entsprechen, das heißt, die ersten und letzten Zeilen der Seiten sollen inhaltlich ungefähr übereinstimmen. Die Idee besteht darin, zunächst in einer *ersten Phase* an den passenden Schnittstellen eine Leerseite einzufügen:

![vav2](https://user-images.githubusercontent.com/101052082/159173745-a3feb20e-29f9-4ac3-9393-520d87b84126.jpg)

Schließlich werden in der *zweiten Phase* die beiden Texte, die nun wie Schloss und Schlüsselloch zusammenpassen, übereinandergelegt, was zum gewünschten Resultat führt:

![vav3](https://user-images.githubusercontent.com/101052082/159174066-4a8d24db-cadd-4683-9f02-5d7c86d029f2.jpg)
<br>
<br>
### Phase 1: Einfügen von Seitenumbrüchen und Leerseiten mit der TUE- bzw. Makrodatei Setze1
In der ersten Phase werden an passenden Stellen der beiden Texte Leerseiten eingefügt. Die ersten bzw. letzten Zeilen der gegenüberliegenden Seiten sollen sich inhaltlich entsprechen. Um dies zu erreichen, müssen die Seitenumbrüche in der Regel manuell gesetzt werden. Jedem Seitenumbruch soll eine Leerseite folgen, damit die Texte in Phase 2 zusammengesetzt werden können. Die Titelseite bildet die erste Seite des linksseitigen Texts **seneca1.tf**.

Dem rechtsseitigen Text **seneca2.tf** werden zuvor zwei Leerseiten vorangestellt, was mit folgender Steueranweisung (bzw. mit einem eigens dafür definierten Makro) erzielt werden kann:  
&lt;np2/&gt;&&&+2&&&{  

Folgende Steueranweisungen fügen einen Seitenumbruch zur nächsten linken oder rechten Seite ein. Wenn auf der beabsichtigten linken Seite ein Umbruch zur nächsten linken Seite eingesetzt wird, so wird automatisch eine Leerseite eingeschaltet. Das Gleiche gilt für die rechte Seite. Die Seitenumbrüche innerhalb eines Textabschnittes bewahren die Zeilenformatierung.
 
<table>
<tr>
    <td>&lt;npl/&gt;&&&l&&&{</td>
    <td>Seitenumbruch zwischen zwei Textabschnitten zur nächsten linken Seite</td>
</tr>
<tr>
    <td>&lt;npr/&gt;&&&r&&&{</td>
    <td>Seitenumbruch zwischen zwei Textabschnitten zur nächsten rechten Seite</td>
</tr>
<tr>
    <td>&lt;npal/&gt;&&l&&{</td>
    <td>Seitenumbruch zur nächsten linken Seite innerhalb eines Textabschnitts</td>
</tr> 
<tr>
    <td>&lt;npar/&gt;&&r&&{</td>
    <td>Seitenumbruch zur nächsten rechten Seite innerhalb eines Textabschnitts</td>
</tr> 
</table>


