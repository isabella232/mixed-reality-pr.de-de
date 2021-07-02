---
title: Codierungsrichtlinien
description: Programmierprinzipien und Konventionen, die bei der Mitwirkung am MRTK befolgt werden müssen.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, C#,
ms.openlocfilehash: c14f5f72d391c5474a01c798bfdaa5529700a509
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175333"
---
# <a name="coding-guidelines"></a>Codierungsrichtlinien

In diesem Dokument werden Codierungsprinzipien und Konventionen beschrieben, die bei der Mitwirkung am MRTK befolgt werden müssen.

---

## <a name="philosophy"></a>Philosophie

### <a name="be-concise-and-strive-for-simplicity"></a>Seien Sie präzise, und achten Sie auf Einfachheit.

Die einfachste Lösung ist häufig die beste. Dies ist ein übergeordnetes Ziel dieser Richtlinien und sollte das Ziel aller Codierungsaktivitäten sein. Ein Teil der Einfachheit ist die Präzise und Konsistenz mit vorhandenem Code. Versuchen Sie, Ihren Code einfach zu halten.

Leser sollten nur auf Artefakte stoßen, die nützliche Informationen bereitstellen. Beispielsweise liefern Kommentare, die das Offensichtliche neu darstellen, keine zusätzlichen Informationen und erhöhen das Rauschen zum Signalverhältnis.

Halten Sie die Codelogik einfach. Beachten Sie, dass es sich hierbei nicht um eine Anweisung zur Verwendung der geringsten Anzahl von Zeilen handelt, um die Größe von Bezeichnernamen oder geschweiften Klammern zu minimieren, sondern um die Reduzierung der Anzahl von Konzepten und die Maximierung der Sichtbarkeit dieser Zeilen durch vertraute Muster.

### <a name="produce-consistent-readable-code"></a>Erstellen von konsistentem, lesbarem Code

Die Lesbarkeit des Codes ist mit niedrigen Fehlerraten korreliert. Versuchen Sie, Code zu erstellen, der einfach zu lesen ist. Versuchen Sie, Code mit einfacher Logik zu erstellen und vorhandene Komponenten erneut zu verwenden, da dies auch zur Gewährleistung der Korrektheit beitragen kann.

Alle Details des Codes, den Sie erzeugen, sind wichtig, von den grundlegendsten Details der Korrektheit bis hin zu konsistentem Stil und konsistenter Formatierung. Halten Sie Ihren Codierungsstil konsistent mit dem, was bereits vorhanden ist, auch wenn er nicht Ihren Wünschen entspricht. Dies erhöht die Lesbarkeit der gesamten Codebasis.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Unterstützung der Konfiguration von Komponenten sowohl im Editor als auch zur Laufzeit

MRTK unterstützt eine Vielzahl von Benutzern: Personen, die Komponenten im Unity-Editor konfigurieren und Prefabs laden möchten, und Personen, die Objekte zur Laufzeit instanziieren und konfigurieren müssen.

Der gesamte Code sollte funktionieren, indem SOWOHL eine Komponente zu einem GameObject in einer gespeicherten Szene hinzugefügt als auch diese Komponente im Code instanziiert wird. Tests sollten einen Testfall sowohl zum Instanziieren von Prefabs als auch zum Instanziieren und Konfigurieren der Komponente zur Laufzeit enthalten.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Play-in-Editor ist Ihre erste und primäre Zielplattform.

Play-In-Editor ist die schnellste Möglichkeit zum Iterieren in Unity. Die Bereitstellung von Möglichkeiten für unsere Kunden, schnell zu iterieren, ermöglicht es ihnen, Lösungen schneller zu entwickeln und weitere Ideen auszuprobieren. Mit anderen Worten: Die Maximierung der Iterationsgeschwindigkeit ermöglicht unseren Kunden, mehr zu erreichen.

Sorgen Sie dafür, dass alles im Editor funktioniert und dann auf jeder anderen Plattform funktioniert. Arbeiten Sie weiterhin im Editor. Es ist einfach, play-in-editor eine neue Plattform hinzuzufügen. Es ist sehr schwierig, play-in-editor funktionsfähig zu machen, wenn Ihre App nur auf einem Gerät funktioniert.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Hinzufügen neuer öffentlicher Felder, Eigenschaften, Methoden und serialisierter privater Felder mit Vorsicht

Jedes Mal, wenn Sie eine öffentliche Methode, ein Feld und eine Eigenschaft hinzufügen, wird sie Teil der öffentlichen API-Oberfläche des MRTK. Private Felder, die mit gekennzeichnet `[SerializeField]` sind, machen felder auch für den Editor verfügbar und sind Teil der öffentlichen API-Oberfläche. Andere Personen können diese öffentliche Methode verwenden, benutzerdefinierte Prefabs mit Ihrem öffentlichen Feld konfigurieren und eine Abhängigkeit davon erstellen.

Neue öffentliche Mitglieder sollten sorgfältig überprüft werden. Jedes öffentliche Feld muss in Zukunft beibehalten werden. Denken Sie daran: Wenn sich der Typ eines öffentlichen Felds (oder eines serialisierten privaten Felds) ändert oder aus einem MonoBehaviour entfernt wird, kann dies andere Personen unterbrechen. Das Feld muss zunächst für ein Release veraltet sein, und Code zum Migrieren von Änderungen für Personen, die Abhängigkeiten übernommen haben, muss bereitgestellt werden.

### <a name="prioritize-writing-tests"></a>Priorisieren des Schreibens von Tests

MRTK ist ein Communityprojekt, das von einer Vielzahl von Mitwirkenden geändert wird. Diese Mitwirkenden kennen möglicherweise nicht die Details Ihrer Fehlerbehebung bzw. Ihres Features und unterbrechen ihr Feature versehentlich. [MRTK führt Continuous Integration-Tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) aus, bevor jeder Pull Request abgeschlossen wird. Änderungen, die Tests unterbrechen, können nicht eingecheckt werden. Daher sind Tests die beste Möglichkeit, um sicherzustellen, dass andere Personen Ihr Feature nicht unterbrechen.

Wenn Sie einen Fehler beheben, schreiben Sie einen Test, um sicherzustellen, dass er in Zukunft nicht zurückgeht. Wenn Sie ein Feature hinzufügen, schreiben Sie Tests, die überprüfen, ob Ihr Feature funktioniert. Dies ist für alle UX-Features mit Ausnahme experimenteller Features erforderlich.

## <a name="c-coding-conventions"></a>C#-Codierungskonventionen

### <a name="script-license-information-headers"></a>Header für Skriptlizenzinformationen

Alle Microsoft-Mitarbeiter, die neue Dateien beitragen, sollten den folgenden Standard-Lizenzheader am Anfang aller neuen Dateien hinzufügen, genau wie unten dargestellt:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>Funktions-/Methodenzusammenfassungsheader

Alle öffentlichen Klassen, Strukturen, Enumerationen, Funktionen, Eigenschaften und Felder, die an das MRTK gesendet werden, sollten entsprechend ihrem Zweck beschrieben und verwendet werden, genau wie unten dargestellt:

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

Dadurch wird sichergestellt, dass die Dokumentation für alle Klassen, Methoden und Eigenschaften ordnungsgemäß generiert und verteilt wird.

Alle Skriptdateien, die ohne ordnungsgemäße Zusammenfassungstags übermittelt werden, werden abgelehnt.

### <a name="mrtk-namespace-rules"></a>MRTK-Namespaceregeln

Das Mixed Reality Toolkit verwendet ein featurebasiertes Namespacemodell, bei dem alle grundlegenden Namespaces mit "Microsoft.MixedReality.Toolkit" beginnen. Im Allgemeinen müssen Sie nicht die Toolkitebene (z. B. Core, Anbieter, Dienste) in Ihren Namespaces angeben.

Die derzeit definierten Namespaces sind:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Boundary
- Microsoft.MixedReality.Toolkit.Diagnostics
- Microsoft.MixedReality.Toolkit.Editor
- Microsoft.MixedReality.Toolkit.Input
- Microsoft.MixedReality.Toolkit.SpatialAwareness
- Microsoft.MixedReality.Toolkit.Teleport
- Microsoft.MixedReality.Toolkit.Utilities

Für Namespaces mit einer großen Anzahl von Typen ist es akzeptabel, eine begrenzte Anzahl von Unternamespaces zu erstellen, um die Bereichsverwendung zu unterstützen.

Wenn Sie den Namespace für eine Schnittstelle, klasse oder einen Datentyp weglassen, wird ihre Änderung blockiert.

### <a name="adding-new-monobehaviour-scripts"></a>Hinzufügen neuer MonoBehaviour-Skripts

Stellen Sie beim Hinzufügen neuer MonoBehaviour-Skripts mit einem Pull Request sicher, dass das [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) -Attribut auf alle anwendbaren Dateien angewendet wird. Dadurch wird sichergestellt, dass die Komponente im Editor unter der Schaltfläche *Komponente hinzufügen* leicht auffindbar ist. Das Attributflag ist nicht erforderlich, wenn die Komponente nicht im Editor angezeigt werden kann, z. B. in einer abstrakten Klasse.

Im folgenden Beispiel sollte das *Paket hier* mit dem Paketspeicherort der Komponente gefüllt werden. Wenn Sie ein Element im *MRTK-/SDK-Ordner* platzieren, ist das Paket *SDK*.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Hinzufügen neuer Unity-Inspektorskripts

Versuchen Sie im Allgemeinen, das Erstellen von benutzerdefinierten Inspektorskripts für MRTK-Komponenten zu vermeiden. Dies erhöht den Mehraufwand und die Verwaltung der Codebasis, die von der Unity-Engine verarbeitet werden kann.

Wenn eine Inspektorklasse erforderlich ist, versuchen Sie, unity zu [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) verwenden. Dies vereinfacht wiederum die Inspektorklasse und überlässt unity einen Großteil der Arbeit.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Wenn benutzerdefiniertes Rendering in der Inspector-Klasse erforderlich ist, versuchen Sie, und zu [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) verwenden. Dadurch wird sichergestellt, dass Unity das Rendern geschachtelter Prefabs und geänderter Werte ordnungsgemäß verarbeitet.

Wenn [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) aufgrund einer Anforderung in der benutzerdefinierten Logik nicht verwendet werden kann, stellen Sie sicher, dass die gesamte Verwendung um eine umschlossen [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) ist. Dadurch wird sichergestellt, dass Unity den Inspektor für geschachtelte Prefabs und geänderte Werte mit der angegebenen Eigenschaft ordnungsgemäß rendert.

Versuchen Sie außerdem, die benutzerdefinierte Inspektorklasse mit einer zu [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) ergänzen. Dieses Tag stellt sicher, dass mehrere Objekte mit dieser Komponente in der Szene zusammen ausgewählt und geändert werden können. Alle neuen Inspektorklassen sollten testen, ob ihr Code in dieser Situation in der Szene funktioniert.

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a>Hinzufügen neuer ScriptableObjects

Stellen Sie beim Hinzufügen neuer ScriptableObject-Skripts sicher, dass das [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) -Attribut auf alle anwendbaren Dateien angewendet wird. Dadurch wird sichergestellt, dass die Komponente im Editor über die Menüs zum Erstellen von Medienobjekten leicht auffindbar ist. Das Attributflag ist nicht erforderlich, wenn die Komponente nicht im Editor angezeigt werden kann, z. B. in einer abstrakten Klasse.

Im folgenden Beispiel sollte der *Unterordner* ggf. mit dem MRTK-Unterordner gefüllt werden. Wenn Sie ein Element im Ordner *MRTK/Providers* ablegen, ist das Paket *Anbieter.* Wenn Sie ein Element im Ordner *MRTK/Core* platzieren, legen Sie dies auf "Profile" fest.

Im folgenden Beispiel *| MyNewProvider* sollte ggf. mit dem Namen Ihrer neuen Klasse ausgefüllt werden. Wenn Sie ein Element im Ordner *MixedRealityToolkit* platzieren, lassen Sie diese Zeichenfolge aus.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Protokollierung

Wenn Sie neue Features hinzufügen oder vorhandene Features aktualisieren, sollten Sie erwägen, DebugUtilities.LogVerbose-Protokolle zu interessantem Code hinzuzufügen, der für das zukünftige Debuggen nützlich sein kann. Es gibt hier einen Kompromiss zwischen dem Hinzufügen der Protokollierung und dem hinzugefügten Rauschen und nicht genügend Protokollierung (was die Diagnose erschwert).

Ein interessantes Beispiel, in dem die Protokollierung nützlich ist (zusammen mit einer interessanten Nutzlast):

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Diese Art der Protokollierung kann dabei helfen, Probleme wie [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) abzufangen, die durch nicht übereinstimmende ermittelte Quell- und Quellverlustereignisse verursacht wurden.

Vermeiden Sie das Hinzufügen von Protokollen für Daten und Ereignisse, die in jedem Frame auftreten. Im Idealfall sollte die Protokollierung "interessante" Ereignisse abdecken, die durch unterschiedliche Benutzereingaben gesteuert werden (d. h. ein "Klick" durch einen Benutzer und der Satz von Änderungen und Ereignissen, die aus stammen, die für die Protokollierung interessant sind). Der fortlaufende Zustand "Benutzer hält immer noch eine Geste" protokolliert jeder Frame ist nicht interessant und überfordert die Protokolle.

Beachten Sie, dass diese ausführliche Protokollierung nicht standardmäßig aktiviert ist (sie muss in den Einstellungen des [Diagnosesystems](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)aktiviert sein).

### <a name="spaces-vs-tabs"></a>Leerzeichen und Registerkarten

Achten Sie darauf, dass Sie 4 Leerzeichen anstelle von Registerkarten verwenden, wenn Sie zu diesem Projekt beitragen.

### <a name="spacing"></a>Abstand

Fügen Sie keine zusätzlichen Leerzeichen zwischen eckigen Klammern und Klammern hinzu:

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>Sie sollten

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>Namenskonventionen

Verwenden Sie immer `PascalCase` für Eigenschaften. Verwenden Sie `camelCase` für die meisten Felder, mit Ausnahme der `PascalCase` Felder und `static readonly` `const` . Die einzige Ausnahme hiervon ist für Datenstrukturen, die erfordern, dass die Felder von serialisiert `JsonUtility` werden.

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>Sie sollten

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>Zugriffsmodifizierer

Deklarieren Sie immer einen Zugriffsmodifizierer für alle Felder, Eigenschaften und Methoden.

- Alle Unity-API-Methoden sollten `private` standardmäßig sein, es sei denn, Sie müssen sie in einer abgeleiteten Klasse überschreiben. In diesem Fall `protected` sollte verwendet werden.

- Felder sollten immer `private` , mit - oder `public` `protected` -Eigenschaftenaccessoren sein.

- Verwenden Von [Ausdruckskörpermembern](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) und [automatischen Eigenschaften](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) nach Möglichkeit

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>Sie sollten

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>Verwenden von geschweiften Klammern

Verwenden Sie nach jedem Anweisungsblock immer geschweifte Klammern, und platzieren Sie sie in der nächsten Zeile.

#### <a name="dont"></a>Nicht empfohlen

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>Sie sollten

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Öffentliche Klassen, Strukturen und Enumerationen sollten alle in ihren eigenen Dateien gespeichert werden.

Wenn die Klasse, Struktur oder Enumeration privat gemacht werden kann, ist es in Ordnung, in derselben Datei enthalten zu sein.  Dadurch werden Kompilierungsprobleme mit Unity vermieden, und es wird sichergestellt, dass eine ordnungsgemäße Codeabstraktion auftritt. Außerdem werden Konflikte und Breaking Changes reduziert, wenn Code geändert werden muss.

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>Sie sollten

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>Empfohlen

MyStruct.cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType.cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass.cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>Initialisieren von Enumerationen

Um sicherzustellen, dass alle Enumerationen ab 0 ordnungsgemäß initialisiert werden, bietet Ihnen .NET eine aufgeräumte Verknüpfung, um die Enumeration automatisch zu initialisieren, indem Sie einfach den ersten Wert (Starter) hinzufügen. (z.B. Wert 1 = 0 Verbleibende Werte sind nicht erforderlich)

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>Sie sollten

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>Reihenfolgenen für die entsprechende Erweiterung

Es ist wichtig, dass, wenn eine Enumeration wahrscheinlich in Zukunft erweitert wird, um Standardwerte am Anfang der Enumeration zu ordnen, dies sicherstellt, dass Enumerationsindizes nicht von neuen Hinzufügungen betroffen sind.

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a>Sie sollten

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a>Überprüfen der Enumerationsverwendung für Bitfelder

Wenn es möglich ist, dass eine Enumeration mehrere Zustände als Wert erfordert, z. B. Handheit = Links & Rechts. Anschließend muss die Enumeration ordnungsgemäß mit BitFlags versehen werden, damit sie ordnungsgemäß verwendet werden kann.

Die Datei "Handedness.cs" verfügt über eine konkrete Implementierung dafür.

### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>Sie sollten

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a>Hart codierte Dateipfade

Gehen Sie wie folgt vor, wenn Sie Zeichenfolgendateipfade generieren und insbesondere hart codierte Zeichenfolgenpfade schreiben:

1. Verwenden Sie nach Möglichkeit die [ `Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) von C#, z. `Path.Combine` B. oder `Path.GetFullPath` .
1. Verwenden Sie / oder [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) anstelle von \ oder \\ \\ .

Diese Schritte stellen sicher, dass MRTK sowohl auf Windows als auch auf Unix-basierten Systemen funktioniert.

### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>Sie sollten

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Bewährte Methoden, einschließlich Unity-Empfehlungen

Einige der Zielplattformen dieses Projekts müssen die Leistung berücksichtigen. Achten Sie vor diesem Hintergrund immer darauf, dass Sie Arbeitsspeicher in häufig aufgerufenem Code in engen Updateschleifen oder Algorithmen zuweisen.

### <a name="encapsulation"></a>Kapselung

Verwenden Sie immer private Felder und öffentliche Eigenschaften, wenn der Zugriff auf das Feld von außerhalb der Klasse oder Struktur benötigt wird.  Stellen Sie sicher, dass Sie das private Feld und die öffentliche Eigenschaft zusammenfinden. Dadurch können Sie auf einen Blick leichter erkennen, was die Eigenschaft unterstützt und ob das Feld durch ein Skript geändert werden kann.

> [!NOTE]
> Die einzige Ausnahme ist dies für Datenstrukturen, die erfordern, dass die Felder von serialisiert werden, wobei eine Datenklasse über alle öffentlichen Felder verfügen `JsonUtility` muss, damit die Serialisierung funktioniert.

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a>Sie sollten

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Zwischenspeichern von Werten und serialisieren sie nach Möglichkeit in der Szene/im Prefab

Im Hinblick auf die HoloLens empfiehlt es sich, die Leistung zu optimieren und Verweise in der Szene oder im Prefab zwischenzuspeichern, um die Speicherbelegung der Laufzeit einzuschränken.

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>Sie sollten

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Zwischenspeichern von Verweisen auf Materialien, nicht jedes Mal ".material" aufrufen

Unity erstellt jedes Mal, wenn Sie ".material" verwenden, ein neues Material, das zu einem Speicherverlust führt, wenn es nicht ordnungsgemäß bereinigt wird.

#### <a name="dont"></a>Sie sollten auf keinen Fall

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a>Sie sollten

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> Verwenden Sie alternativ die Unity-Eigenschaft "SharedMaterial", die nicht jedes Mal, wenn darauf verwiesen wird, ein neues Material erstellt.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>Verwenden der [plattformabhängigen Kompilierung,](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) um sicherzustellen, dass das Toolkit den Build auf einer anderen Plattform nicht unterbricht

- Verwenden Sie `WINDOWS_UWP` , um UWP-spezifische, nicht Unity-APIs zu verwenden. Dadurch wird verhindert, dass sie versuchen, im Editor oder auf nicht unterstützten Plattformen auszuführen. Dies entspricht `UNITY_WSA && !UNITY_EDITOR` und sollte zugunsten von verwendet werden.
- Verwenden Sie `UNITY_WSA` , um UWP-spezifische Unity-APIs wie den Namespace zu `UnityEngine.XR.WSA` verwenden. Dies wird im Editor ausgeführt, wenn die Plattform auf UWP festgelegt ist, sowie in integrierten UWP-Apps.

Dieses Diagramm kann Ihnen bei der Entscheidung helfen, welche Sie `#if` verwenden möchten, abhängig von Ihren Anwendungsfällen und den erwarteten Buildeinstellungen.

|Plattform | UWP IL2CPP | UWP .NET | Editor |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | Falsch | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | Falsch |
| `NETFX_CORE` | False | True | Falsch |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>"DateTime.UtcNow" gegenüber "DateTime.Now" bevorzugen

DateTime.UtcNow ist schneller als DateTime.Now. In vorherigen Leistungsuntersuchungen haben wir festgestellt, dass die Verwendung von DateTime.Now einen erheblichen Mehraufwand verursacht, insbesondere bei Verwendung in der Update()-Schleife. [Andere haben das gleiche Problem.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)

Verwenden Sie DateTime.UtcNow, es sei denn, Sie benötigen tatsächlich die lokalisierten Zeiten (ein legitimer Grund kann sein, dass Sie die aktuelle Uhrzeit in der Zeitzone des Benutzers anzeigen möchten). Wenn Sie mit relativen Zeiten (d. h. dem Delta zwischen dem letzten Update und dem aktuellen Update) arbeiten, sollten Sie DateTime.UtcNow verwenden, um den Mehraufwand für Zeitzonenkonvertierungen zu vermeiden.

## <a name="powershell-coding-conventions"></a>PowerShell-Codierungskonventionen

Eine Teilmenge der MRTK-Codebasis verwendet PowerShell für die Pipelineinfrastruktur und verschiedene Skripts und Hilfsprogramme. Neuer PowerShell-Code sollte dem [PoshCode-Stil folgen.](https://poshcode.gitbooks.io/powershell-practice-and-style/)

## <a name="see-also"></a>Siehe auch

 [C#-Codierungskonventionen von MSDN](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
