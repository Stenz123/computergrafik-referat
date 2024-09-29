# Referat Computergrafik
Michael Stenz

## (3D) Rendering Algorithmen
### Allgemein
Rendering ist der Prozess, bei dem eine 2D- oder 3D-Szene in ein Bild umgewandelt wird. Dieser Prozess wird durch Rendering-Algorithmen durchgeführt. Grundsätzlich ist es egal ob es sich um 2D oder 3D handelt, beide müssen trotzdem mit einem Algorithms durch einen dargestellt werden, allerdings werde ich in diesem Abschnitt eher auf 3D Rendering eingehen, da diese Berechnung um einiges Komplexer ist. Außerdem kann in zwei große Kategorien unterteilt werden: realtime rendering und nicht non realtime rendering.

### Real Time Rendering

Real-time-Rendering wird häufig in interaktiven Medien wie Videospielen und Simulationen verwendet, da die Bilder in Echtzeit berechnet und dargestellt werden müssen, um eine flüssige Wiedergabe zu gewährleisten. Dabei liegt die Bildrate typischerweise zwischen 20 und 120 FPS (frames per second). Um eine flüssige Bewegung wahrzunehmen, ist eine Mindestbildrate von etwa 24 FPS erforderlich, da alles darunter als ruckelig empfunden wird. Es gibt jedoch Techniken, die unsere Wahrnehmung austricksen können, indem sie Effekte nutzen, die das Gehirn als flüssig interpretiert, auch wenn sie nicht der Realität entsprechen.

Ein Beispiel hierfür ist der Motion Blur, bei dem bewegte Objekte verschwommen dargestellt werden, um den Eindruck flüssiger Bewegungen zu erzeugen. Weitere solcher Techniken sind Temporal Anti-Aliasing (TAA), Schärfentiefe (Depth of Field), Bloom, Ambient Occlusion, Screen Space Reflections und Screen Space Global Illumination. Durch diese Effekte wirkt die Darstellung trotz technischer Limitierungen realistischer.

Außerdem werden in Spielen oft visuelle Effekte genutzt, die eigentlich nur bei Kameras auftreten, wie Lens Flares, chromatische Aberration oder Vignetten-Effekte. Diese Effekte sind zwar nicht Teil der natürlichen menschlichen Wahrnehmung, aber unser Gehirn erkennt sie aus der Film- und Fotowelt wieder und interpretiert sie als realistisch.

Die steigende Rechenleistung von Computern, insbesondere durch den Einsatz leistungsstarker Grafikprozessoren (GPUs), ermöglicht es, immer realistischere Bilder in Echtzeit darzustellen. Methoden wie Raytracing, das Lichtstrahlen realistisch simuliert, sowie volumetrisches Licht und High Dynamic Range (HDR)-Rendering haben die Qualität von Echtzeitdarstellungen erheblich verbessert.


### Non Real Time Rendering / Offline Rendering

Im Gegensatz zum Real-Time-Rendering wird beim -Rendering die Bildqualität höher priorisiert als die Geschwindigkeit. Dies bedeutet, dass die Bilder nicht in Echtzeit berechnet werden müssen, sondern so lange, wie es dauert, um die bestmögliche Qualität zu erzielen. Rendering zeiten können hier von einigen Sekunden pro Bild, bis zu mehreren Tagen dauern. Dieser Prozess wird oft in der Filmproduktion, Architekturvisualisierung, medizinischen Bildgebung und wissenschaftlichen Visualisierung verwendet. Da die Bilder nicht in Echtzeit berechnet werden müssen, können komplexere Algorithmen und Techniken verwendet werden, um realistischere Bilder zu erzeugen.

Für Fotorealistische Bilder werden oft Algorithmen wie Raytracing, Pathtracing oder Radiosity verwendet. Diese Algorithmen simulieren die Ausbreitung von Lichtstrahlen in einer Szene und berechnen, wie das Licht von den Objekten reflektiert, gebrochen und absorbiert wird. Dadurch können realistische Schatten, Spiegelungen, Lichtbrechungen und Farben erzeugt werden. Diese Algorithmen wurden entwickelt, um auch komplexe physikalische interaktion von Licht und Gegenständen zu simulieren, wie in etwa die Brechung des Lichts durch Wasser bzw Glas. Ein aus der Realität für diese Art an komplexen Lichtbrechungen, sind die Lichtformen, die am Boden eines Swimmingpools zu sehen sind (Kaustik), oder wie Licht durch dünne Hautstellen durchdringt (Subsurface scattering). Auch wenn man diese Effekte aus Videospielen kennt, sind dies Meistens nur vereinfachte Versionen dieser Effekte, um Rechenleistung zu sparen.

Obwohl sich die Hardware für Rendering stetig verbessert benötigen größere Filmstudios, die mit Computeranimationen arbeiten trotzdem meistens ganze Renderfarmen. Jedoch wird es als Privatperson immer einfacher, mit Programmen wie Blender, Cinema 4D oder der Unreal Engine realistische Bilder zu erstellen.

![caustic](https://developer-blogs.nvidia.com/wp-content/uploads/2020/12/featured_image.jpg)

https://en.wikipedia.org/wiki/3D_rendering

### Zukunft des Renderings
Mit der stetigen Weiterentwicklung von GPUs und Rendering-Technologien schreitet auch die Qualität der Echtzeit-Visualisierung voran. Zukünftige Entwicklungen wie Echtzeit-Raytracing, KI-gestützte Rendering-Optimierungen und der Einsatz von Cloud-Rendering-Diensten könnten Echtzeit-Rendering zugänglicher und qualitativ noch hochwertiger machen.

### HDR Rendering
High Dynamic Range Rendering (HDR), auch oft bekannt unter High Dynamic Range Lighting ist eine Technik. Diese Technik ermöglicht die Bewahrung von Details, die durch begrenzte Kontrastverhältnisse verloren gehen könnten. Im Vergleich zu den herkömmlichen 256 Helligkeitsstufen pro Farbkanal werden bei HDRR die Farben intern mit einer so hohen Präzision dargestellt, dass ein sehr großer Helligkeitsbereich abgedeckt werden kann. Dadurch lassen sich starke Kontraste darstellen, ohne dass dabei zu viele Details verloren gehen. Eine besondere Technik aus dem HDRR-Bereich  ist das Image-based Lighting, bei dem eine Computergrafik-Szene durch ein HDR-Bild umhüllt und beleuchtet wird. Dadurch entsteht der Eindruck, die künstlich modellierten Objekte würden in eine natürliche Umgebung eingefügt.

HDRR kann auch Hardware unterstützt werden in dem die Grafikkarte intern für eine Farbe einen höheren Helligkeitsbereich abspeichert. Dies resultiert darin, dass eine einzelne Farbinformation mehr Speicherplatz benötigt. Wenn dies nicht gegeben wäre, würden farbverläufe zu grob werden bzw. man würde große Sprünge/Artefakte erkennen. Da nach diesem Prozess die Farben wieder auf 8 Bit pro Kanal reduziert werden, wird ein Prozess namens Tone Mapping (Dynamikkompression) durchgeführt. Dieser Prozess ist dafür zuständig, dass Farben die über ein großes Helligkeitsspektrum verteilt sind, auf ein kleineres Spektrum reduziert werden.

Zusammenfassend ist der Vorteil von HDRR, dass sowohl sehr helle als auch sehr dunkle Bildbereiche erhalten bleiben, ohne durch den begrenzten Helligkeitsumfang zu stark eingegrenzt zu werden, sodass diese nicht als reines Schwarz oder Weiß erscheinen.

Einige Beispiele wo HDRR angewendet wird, sind Far Cry, Counter-Strike, Project Gotham Racing 3, Halo 3 und ab der Unreal Engine 3.

![image](https://upload.wikimedia.org/wikipedia/en/8/89/Lost_Coast_HDR_comparison.png)


### Raytracing
Das Wort Raytracing setzt sich aus den englischen Wörtern "ray" (Strahl) und "tracing" (verfolgen) zusammen. Raytracing ist ein Algorithmus, der die Ausbreitung von Lichtstrahlen in einer Szene simuliert, er berechnet die Sichtbarkeit von dreidimensionalen Objektion von einem Bestimmten Punk aus. Dabei wird ein Strahl von der Kamera aus durch jeden Pixel des Bildschirms geschossen und verfolgt, wie er durch die Szene verläuft. Wenn der Strahl auf ein Objekt trifft, wird berechnet, wie das Licht von diesem Objekt reflektiert, gebrochen oder absorbiert wird. Dadurch können realistische Schatten, Spiegelungen, Lichtbrechungen und Farben erzeugt werden. Raytracing ist besonders gut geeignet, um komplexe Lichteffekte wie Kaustiken, Subsurface Scattering und globale Beleuchtung zu simulieren.

Als Entwickler des Raytracing Algorithmus gelten Herb Steinberg, Marty Cohen und Eugene Troubetskoy, die den Algorithmus ende der 1960er Jahren veröffentlichten. Anders als die "Vorgänger" von Raytracing die einfach nur Schattierungen von beleuchteten Objekten im dreidimensionalen Rauch nachahmten, hatte nun Raytracing einen physikalischen Hintergrund. Ganz einfache Formen des Raytracing verwenden nur, dass direkte Licht der Lichtquelle, allerdings wurde der Algorithmus über die Jahre dauernd erweitert.

#### Funktionsweise
##### Erste annäherung
Das endgültige Ziel des Raytracing verfahrens ist, aus dem 3D Modell oder aus einer 3D-Landschaft ein 2D Bild zu generieren. Dieses Bild besteht logischerweise aus Pixeln, die wiederum aus Farben bestehen. Also ist im endeffekt, dass endgültige Ziel des Raytracing Algorithmus, die Farbe eines Pixels zu berechnen. In einer vereinfachten ersten annäherung kann man um die Farbe eines Pixels zu berechnen, einfach den Durchschnitt er Farben aller Lichtstrahlen nehmen, die die Kamera treffen. In diesem Modell, und in allen darauf folgenden kann man von der die Kamera wie eine Lochkamera sehen. Allerdings, wird unsere erste Annäherung nicht sehr realistisch sein, da wir keine Schatten, Spiegelungen oder Lichtbrechungen haben.  
 
##### Verfolgen von Lichtstrahlen
Wie schon vorher geklärt braucht man, um die Farbe eines Pixels zu berechnen, die Farbe des Lichtstrahls der die Kamera trifft. Deshalb werden die Lichtstrahlen als klassische Photonen dargestellt. Diese werden wie in der Realität behandelt, dass heißt wenn ein grünes und ein rotes Photon auf unser Auge gleichzeitig triff wird dies als gelb wahrgenommen. Um nun einmal vereinfachtes Raytracing an einem Beispiel zu zeigen (Abb. ). Hier ist ein Wohnzimmer mit einer Lampe gezeigt. Strahl A trifft die Wand, und wird fast vollständig absorbiert. Dies könnte einige Gründe haben, wie zum Beispiel die Oberfläche der Wand. Strahl B hingegen wird 2 mal von reflektiert und landet danach in der Kamera, wohingegen Strahl C direkt reflektiert wird und in der Kamera landet. Strahl E wird erreicht die Kamera nie. Sehen Sie sich nun mal im Raum um und überlegen Sie doch von wo das Licht reflektiert wird. Wenn man in den Spiegel blickt, funktioniert dieses Selbstexperiment ebenso sehr gut. Sie haben gerade Raytracing durchgeführt.

![img](./img/light-bounce.png)

##### Vorwärts und Rückwärtsverfolgung der Strahlen
Es gibt zwei Arten von Raytracing, die Vorwärts- und die Rückwärtsverfolgung. Vorwärts, wäre, wenn man alle Lichtstrahlen ausgehend von Jeder Lichtquelle verfolgt, wie in unserem vorherigen Beispiel. Dieser Ansatz mag sich zwar sehr logisch anhören, allerdings wird die Komplexität sehr viel unnötige Information berechnet. D.h jede einzelne Lichtquelle stößt Millionen von Photonen aus, jedes einzelne mit einer etwas anderen Frequenz und richtung. Die meisten dieser Photonen werden niemals die Kamera erreichen. Mit einer solchen komplexität der Berechnung viel zu teuer und man könnte sogar mit Berechnungszeiten von einigen Jahren rechnen.

Um dieses Problem effizienter zu lösen, betrachtet man die Situation aus der Sicht der Kamera. Alle relevanten Photonen sind nur jene, die auch wirklich die Kamera treffen. Dabei wird ermittelt, welches Objekt entlang des Strahls getroffen wird und woher das Licht kommt, das dieses Objekt beleuchtet.

##### Schatten
Für die Berechnung von Schatten werden sogenannte Shadow Rays verwendet. Diese Strahlen gehen von einem Punkt auf der Oberfläche eines Objekts in Richtung einer Lichtquelle. Wenn der Strahl die Lichtquelle ungehindert erreicht, wird der Punkt beleuchtet. Wenn jedoch ein anderes Objekt im Weg ist, wird das Licht blockiert, und der Punkt liegt im Schatten. Shadow Rays dienen also dazu, zu überprüfen, ob Licht eine Oberfläche erreicht oder nicht. Wenn ein Strahl erfolgreich zur Lichtquelle gelangt, wird er als Illumination Ray betrachtet, der Licht auf den Punkt bringt.

Shadow Rays werden an jedem Punkt gesendet, an dem ein Primärstrahl ein Objekt trifft, also überall dort, wo das Raytracing die Oberfläche eines Objekts berührt. Dieser Punkt repräsentiert einen potenziell sichtbaren Teil der Szene, der ausgeleuchtet werden muss. Um zu entscheiden, ob der Punkt beleuchtet oder im Schatten liegt, wird von diesem Punkt aus ein Shadow Ray zu jeder Lichtquelle geschickt. Diese Rays werden immer in Richtung jeder Lichtquelle geschickt. 

Reflektierende Objekte und Transparenz brauchen allerdings noch Zusätzliche Berechnungen.

![shadow-ray](./img/shadow-ray.png)

##### Reflection
Reflexionsstrahlen (Reflection Rays) entstehen, wenn Licht auf eine glänzende oder spiegelnde Oberfläche trifft und in eine neue Richtung abgelenkt wird. An einem gegebenen Punkt auf der Oberfläche gibt es für eine feste Betrachterposition immer nur eine Richtung, aus der das Licht kommen kann, das in Richtung der Kamera reflektiert wird.

Um den Farbwert des reflektierten Lichts zu berechnen, wird ein Strahl entlang des reflektierten Winkels zurückverfolgt, um festzustellen, von welchem Objekt das Licht ursprünglich gekommen ist. Die Farbe des reflektierten Lichts wird von dem Objekt bestimmt, das entlang des Strahls getroffen wird. Diese Farbe trägt dann zur Gesamtfarbe des Punktes bei, die wir im Bild sehen.

##### Transparenz
Um die Farbe des Lichtes zu bestimmen, das durch die transparente Oberfläche übertragen wird, wird der Transparenzstrahl rückverfolgt. Dabei wird untersucht, welches Objekt das Licht ursprünglich ausgestrahlt hat und in welche Richtung es gesendet wurde. Durch die Beugung oder Brechung des Lichts, wenn es von einem Medium in ein anderes übertritt, wird sichergestellt, dass der Farbwert des übertragenen Lichts korrekt erfasst wird. Sobald die Farbe des ursprünglichen Objekts bekannt ist, kann diese zur Gesamtfarbe des einfallenden Lichtstrahls hinzugefügt werden.

##### Praktische Umsetzung
In den vorherigen Kapiteln wurde erklärt, wie die Farbe der Lichtstrahlen, die an verschiedenen Objekten reflektiert oder durchscheinend sind, berechnet wird. Die Farbe des Lichts, das von einer Oberfläche ausgeht, ist eine Kombination aus Lichtquellen, reflektiertem und durchscheinendem Licht. Um diese Farben zu bestimmen, analysieren wir die Objekte, von denen die Lichtstrahlen ausgehen.

Diese Beobachtung bringt uns zu einem klassischen Algorithmus aus der Informatik: einem rekursiven Algorithmus. Wir beginnen mit einem Lichtstrahl aus der bei der Kamera starte und bei jeder Interaktion bestimmen wir die Farbe der Lichtstrahlen und setzen den Prozess fort, indem wir reflektiertes oder durchscheinendes Licht berücksichtigen. So entsteht eine realistische Darstellung der Szene. Um dies etwas besser zu veranschaulichen hier ein Beispiel mit Pseudocode:

```
function traceImage (scene) {
    for each pixel (i,j) in image { // i und j sind die Indexe bzw. Koordinaten der Pixel
        A = pixelToWorld(i,j) // Wir brauchen die Position des Pixels in unserer 3D umgebung.
        P = COP // Center of Projection. Dies ist der Punkt von dem aus die Kamera schaut. Siehe Lochbildkamera
        d = (A - P)/|| A – P|| // Richtung des Strahls
        I(i,j) = traceRay(scene, P, d) // Berechnung der Farbe des Pixels
    }
}
```


```
function traceRay(scene, P, d):
    (t, N, mtrl) = scene.intersect (P, d) // t ist der Abstand zum nächsten Objekt, N ist die Normale des Objekts und mtrl ist das Material des Objekts
    Q = ray (P, d) evaluated at t // Q ist der Punkt an dem der Strahl das Objekt trifft
    I = shade(mtrl, scene, N, Q, d)
    return I
end function
```

```
function shade(mtrl, scene, Q, N, d){
    //Startlichtintensität des Objekts
    I = mtrl.k_e + mtrl.k_a * I_La // k_e ist die Emmisionskomponent (wieviel Licht strahlt das Material aus), k_a ist die Ambientskomponente (wie gut Reflektiert, das Material) und I_La ist die Intensität des Lichts/Umgebungslichts
    // I ist die Gesamthelligkeit an Punk Q
    for each light source L do {
        atten = L -> distanceAttenuation(Q) // Wie stark wird das Licht abgeschwächt (Dämpfung)
        I = I + atten * (diffuse term + specular term) 
    }
    return I
}
```

Zunächst wird für jedes Pixel im Bild die Position in der 3D-Umgebung ermittelt. Ausgehend von der Kamera wird ein Lichtstrahl in die Szene gesendet. Der Richtungsvektor dieses Strahls wird so berechnet, dass er auf das entsprechende Pixel zeigt. Bei der Interaktion des Lichtstrahls mit Objekten in der Szene wird der Punkt bestimmt, an dem der Strahl auf ein Objekt trifft, sowie die Normale an dieser Stelle und das Material des Objekts. An diesem Punkt wird die Lichtintensität berechnet, die von diesem Objekt reflektiert oder emittiert wird. Für jede Lichtquelle in der Szene wird die Lichtintensität berechnet, die von dieser Lichtquelle auf den Punkt trifft. Dabei wird die Dämpfung des Lichts durch die Entfernung zur Lichtquelle berücksichtigt. Die Gesamthelligkeit des Punktes wird als Summe der Beiträge aller Lichtquellen zurückgegeben. Hier werden allerdings noch keine Schatten und Reflexion berücksichtigt, allerdings lässt sich dies einfach implementieren, indem man die shadow() funktion bearbeitet und eine neue shadowAttenuation() Funktion hinzufügt.

```
function PointLight::shadowAttenuation(scene, P){
    d = (this.position - P).normalize // *Siehe formel unten    
    (t, N, mtrl) = scene.intersect(P, d) // Abstand, Normalvektor und Material des getroffenen Objekts
    Compute t_light // Abstand zur Lichtquelle
    if (t < t_light) { // Wenn der Abstand zum getroffenen Objekt kleiner ist als der Abstand zur Lichtquelle
        atten = (0, 0, 0) // Dann ist der Punkt im Schatten
    else
        atten = (1, 1, 1) // Sonst ist der Punkt beleuchtet
    }
    return atten
}
```
\*
$\frac{L_{P} - P}{|L_{P} - P|}$

Hier wird nun der Vektor in Richtung Licht berechnet, und dann noch überprüft ob ein Objekt im Weg ist. Wenn ja, dann ist der Punkt im Schatten, wenn nicht, dann ist der Punkt beleuchtet. Dieses Prinzip der sogenannten Shadow Rays wurde oben schon beschrieben.

Und wenn wir diese Funktion jetzt noch in unsere ursprüngliche shade Funktion einbauen, haben wir nun auch Schatten in unserer Szene.

```
function shade(mtrl, scene, Q, N, d){
    I = mtrl.k_e + mtrl.k_a * I_La
    for each light source L do {
        atten = L -> distanceAttenuation(Q) * shadowAttenuation(scene, Q) // we just multiply this with the result of the shadowAttenuation function (0 or 1)
        I = I + atten * (diffuse term + specular term) 
    }
    return I
}
```

### Pathtracing

### Radiosity

## Computergrafik Allgemein


## Grafikkarten

## Grafik & Betriebssysteme
https://lwn.net/Articles/955376/

## Grafiken erstellen

## Quellen
https://developer.nvidia.com/blog/generating-ray-traced-caustic-effects-in-unreal-engine-4-part-1/

https://developer.nvidia.com/gpugems/gpugems/part-iii-materials/chapter-16-real-time-approximations-subsurface-scattering

[An Introduction to Ray Tracing - Anrew S. Glassner](https://www.realtimerendering.com/raytracing/An-Introduction-to-Ray-Tracing-The-Morgan-Kaufmann-Series-in-Computer-Graphics-.pdf)

[University Washington - Raytracing](https://courses.cs.washington.edu/courses/cse457/11au/lectures/markup/ray-tracing-markup.pdf)