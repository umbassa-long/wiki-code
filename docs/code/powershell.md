https://qualidy.github.io/wiki-powershell/

Get-Process 'some process' | Format-Table Name, CPU | Select-Object Name, CPU

Get-History | Export-Csv -Path C:\testing\history.csv -IncludeTypeInformation
Import-Csv -Path C:\testing\history.csv | Add-History

https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/add-history?view=powershell-7.5&viewFallbackFrom=powershell-6


Finden Sie heraus, welche Befehle das Verb Import verwendet.
Welche Eigenschaften von Diensten auf Ihrem Rechner kann das Cmdlet Get-Service
anzeigen?
Recherchieren Sie mit den im Kapitel vorgestellten Mitteln
a) die Syntax des Cmdlets Get-Module,
b) Beispiele zum Einsatz des Cmdlets Get -PSDrive,
c) was der Parameter -Format des Cmdlets Get-Date bedeutet.
Lesen Sie die vollstandigen Hilfetexte zu den vorgestellten Get-Befehlen Get-History,
Get-Process und Get-PSProvider.
Finden Sie heraus, welche Eigenschaften Ihnen für das Cmdlet Get -Module zur Verfügung
stehen.



ForEach-Object
Group-Object
Measure-Object
Select-Object
Sort-Object
Tee-Object
Where-Object

Daten Sammeln

Ergebnisse bearbeiten

Ergebnisse ausgeben

Get -...

...- Object

Export -... , Format -... , Out -...

Get-Process -Name powershell | Select-Object -Property Id, ProcessName

Get-EventLog -LogName System -Newest 20 | Sort-Object -Property InstanceID

Get-ChildItem -File | Sort-Object -Property Extension, Length
 
Größe der Datei, Name der Datei, Endung
 
Get-ChildItem -File | Select-Object -Property Extension, Length, Name
 
 Get-ChildItem -File | Where-Object Length -LT 100
 
Get-ChildItem -File | Where-Object Length -GT 1MB

Get-ChildItem -File | Where-Object Length -LE 1000 | Where-Object Length -GT 100
 
Get-ChildItem -File | Where-Object {$_.Length -LT 1000 -and $_.Length -GT 100}
 
 Get-ChildItem -File | Where-Object Length -LE 1000 | Where-Object Length -GT 100 | Sort-Object Length | Select-Object Length, Name

 1..3 | ForEach-Object -Process { Test-Connection 127.0.0.$_ -Count 1}

 100..102 | ForEach-Object -Process { $_ * 2 }
 
"google.com", "heise.de" | ForEach-Object -Process { Test-Connection $_ }
 
"Server1", "Server2", "PC5" | ForEach-Object -Process { Stop-Computer -ComputerName $_ -WhatIf}
 
 Select wählt nach Attributen aus - Where sortiert Dateien

 Get-ChildItem -File | Group-Object -Property Extension
 
Get-ChildItem -File | Group-Object -Property Extension | Sort-Object count
 
Get-ChildItem -File | Group-Object -Property Extension | Sort-Object count -Descending

 
Get-ChildItem -File | Group-Object -Property Extension | Where-Object count -gt 1
 
 Get-ChildItem -File | Measure-Object Length -Sum -Average -Minimum -Maximum

 
10, 20, 23, 65, 39, 50, -40, 12 | Measure-Object -Sum -Average -Minimum -Maximum
 
 Get-ChildItem -File *.png | Measure-Object Length -Average

 Get-ChildItem -File | `

Group-Object Extension | `

Select-Object @{n='Extension';e={ if([string]::IsNullOrEmpty($_.Name)) {'[ohne Endung]'} else {$_.Name.ToLower() }}}, `

              @{n='AvgMB';e={[math]::Round((($_.Group | Measure-Object Length -Average).Average/1MB),2)}}, `

              @{n='Count';e={$_.Count}} | `

Sort-Object AvgMB -Descending
 
Get-Content dienste.txt | Measure-Object -Line -Word -Character
 
 Get-ChildItem -File *.txt | ForEach-object { Get-Content $_ | Measure-Object -Line -Word -Character }

 Get-ChildItem -File | Tee-Object -Variable allFiles | Where-Object Extension -EQ ".css"

 Get-ChildItem -File | Where-Object Length -LT 100 | Out-Gridview

 Get-ChildItem -file | Where-Object length -lt 100 | out-file my-output.txt

 Get-ChildItem -File | Where-Object { $_.Length -LE 100 }
 
$my_array = 2, 3, 4, 6, 19, "hallo", -23
 
$my_array
 
leere arrays: 
$my_array = @()

$my_array
 
einelementige arrays: 
$my_array = @(12)

$my_array
 
mehrelementige arrays:
$my_array = @(12, 13, 14)

$my_array
 
$my_array = 1,2,3,2,1,0

$my_array.Count
 
$my_array = 1,2,3,2,1,0

$my_array[0] = 7

$my_array
 
vergrößerung des arrays 
 
$my_array = 1,2,3,2,1,0

$my_array += 7

$my_array
 
wert überschreiben:
$my_array = 1,2,3,2,1,0

$my_array.SetValue(25,0)

$my_array
 
oder: 
$my_array = 1,2,3,2,1,0

$my_array[0] = 25

$my_array
 
$a = 10

$b = 12
 
$c = $a * $b

$c
 
$c = 0

++$c

$c
 
$c = 0

$c = $c - 1

$c
 
$c = 0

$c += 1

$c

### 1Operator

-eq

-ne

-gt

-ge

-1t

-le

-Contains

-NotContains

### 2Bedeutung

Ist gleich
(equal to)
Ist ungleich
(not equal to)
Größer als
(greater than)
Größer oder gleich 2 -ge 3 (Ergebnis: FALSE)
(greater than or
equal to)
Kleiner als
(less than)
Kleiner oder gleich
(less than or
equal to)
Prüft eine gege-
bene Werteliste,
ob ein Wert ent-
halten ist

Umkehrung
des Operators
-Contains

### 3Beispiele
2 -eq 3 (Ergebnis: FALSE)
"Harry" -eq "harry" (Ergebnis: TRUE)
2 -ne 3 (Ergebnis: TRUE)
"Harry" -ne "harry" (Ergebnis: FALSE)
2 -gt 3 (Ergebnis: FALSE)
"Harry" -gt "harry" (Ergebnis: FALSE)

"Harry" -ge "harry" (Ergebnis: TRUE)

2 -1t 3 (Ergebnis: TRUE)
"Harry" -1t "harry" (Ergebnis: FALSE)
2 -le 3 (Ergebnis: TRUE)
"Harry" -le "harry" (Ergebnis: TRUE)

"abc ", "def " -Contains "abc"
(Ergebnis: TRUE)
"abc ", "def " -Contains "bc"
(Ergebnis: FALSE)
"abc ", "def " -NotContains "abc"
(Ergebnis: FALSE)
"abc ", "def " -NotContains "bc"
(Ergebnis: TRUE)


### 2Operator

-In

-NotIn

-Is

-IsNot

-Like

-NotLike

### 2Bedeutung

Wie -Contains,
nur in umgekehr-
ter Reihenfolge
Umkehrung des
Operators -In

Prüfung auf Typ-
gleichheit
Umkehrung des
Operators -Is
Einfacher Text-
abgleich; prüft,
ob sich eine Zei-
chenkette in einer
anderen befindet

Umkehrung des
Operators -Like

### 2Beispiele
"abc " -In "abc", "def" (Ergebnis: TRUE)
"bc " -In "abc", "def " (Ergebnis: FALSE)

"abc " -NotIn "abc", "def"
(Ergebnis: FALSE)
"bc " -NotIn "abc", "def " (Ergebnis: TRUE)
[string] $string = "Herdt-Verlag"
$string -Is [string] (Ergebnis: TRUE)
[string] $string = "Herdt-Verlag"
$string -IsNot [string] (Ergebnis: FALSE)
"abcdef " -Like "abc" (Ergebnis: FALSE)
"abcdef " -Like "abc*" (Ergebnis: TRUE)
"abcdef " -Like "*c*" (Ergebnis: TRUE)

-Match

-NotMatch

Suche nach
Substring ohne
Wildcards (auch
Mustervergleich
mit regulären
Ausdrücken)

Umkehrung
des Operators
-Match

"abcdef " -NotLike "abc" (Ergebnis: TRUE)
"abcdef " -NotLike "abc*"
(Ergebnis: FALSE)
"abcdef " -NotLike "*c*" (Ergebnis: FALSE)
"abcdef " -Match "c" (Ergebnis: TRUE)

"abcdef " -NotMatch "c" (Ergebnis: FALSE)

### 3Operatoren


-and

Bedeutung

Alle Einzelbedingungen
müssen erfüllt sein.

-or

Mindestens eine der Einzel-
bedingungen muss erfüllt
sein.

-xor

Genau eine der Einzel-
bedingungen muss erfüllt
sein, nicht aber mehrere
oder alle.

### 3Beispiele
( (2 -gt 3) -and (2 -gt 1) -and
(0 -gt -1) )
(Ergebnis: FALSE)
( (2 -gt 3) -or (2 -gt 1) -or
(0 -gt -1) )
(Ergebnis: TRUE)

( (2 -gt 3) -xor (2 -gt 1) -xor
(0 -gt 1) )
(Ergebnis: TRUE)

mehr beispiele
$names = "Bernd", "Clara", "Domenik", "Frieda", "Günther", "Rachel"
 
$names | Where-Object { $_ -LT "e" }
 
$names =@("Bernd", "Clara", "Domenik", "Frieda", "Günther", "Rachel")
 
$names | Where-Object { $_ -LT "e" }
 
$names =@("Bernd", "Clara", "Domenik", "Frieda", "Günther", "Rachel")
 
$names | Where-Object { $_ -like "*a*" }
 
$names =@("Bernd", "Clara", "Domenik", "Frieda", "Günther", "Rachel")
 
$names | Where-Object { $_ -match "a" }
 
$dateien = Get-ChildItem -File
 
$dateien | Select-Object Name, Length | Where-Object {$_.Name -gt "L"}
 
#Select: welche spalten?

#where: welche zeilen?


Compare-Object (get-content .\Testfile1.txt) (get-content .\Testfile2.txt) -IncludeEqual
 
Compare-Object (get-content .\Testfile1.txt) (get-content .\Testfile2.txt) -IncludeEqual | where-Object sideindicator -eq "<="
$o1 = Get-ChildItem .\ordner1
$o2 = Get-ChildItem .\ordner2
 
Compare-Object $o1 $o2 -IncludeEqual

$argument = @{ DifferenceObject = get-childitem .\ordner1; ReferenceObject = get-childitem .\ordner2 }
 
$argument.DifferenceObject

$argument = @{ IncludeEqual =$true; DifferenceObject = get-childitem .\ordner1; ReferenceObject = get-childitem .\ordner2 }
 
Compare-Object @argument
 
# Listen vorbereiten

$A = Get-ChildItem .\ordner1 -File | Select-Object -Expand Name

$B = Get-ChildItem .\ordner2 -File | Select-Object -Expand Name
 
# Diff berechnen

$diff = Compare-Object $A $B
 
# Ergebnisse

$nurIn1 = $diff | Where-Object SideIndicator -eq '<=' | Select-Object -Expand InputObject

$nurIn2 = $diff | Where-Object SideIndicator -eq '=>' | Select-Object -Expand InputObject

$inBeiden = Compare-Object $A $B -IncludeEqual | Where-Object SideIndicator -eq '==' | Select-Object -Expand InputObject
 
# Anzeigen

"Nur in ordner1:", $nurIn1

"Nur in ordner2:", $nurIn2

"In beiden:", $inBeiden

 Get-ChildItem -Path $root -Filter *.png -Recurse -File -ErrorAction SilentlyContinue | ForEach-Object { $size = $.Length $target = switch { $size -lt 100 { $dest1 } ($size -ge 1000) -and ($size -lt 10000) { $dest2 } $size -ge 10000 { $dest3 } default { $null } } if ($target) { Copy-Item -Path $.FullName -Destination $target -Force } }

 Get-ChildItem -Path $root -Filter *.png -Recurse -File -ErrorAction SilentlyContinue |
ForEach-Object {
    $size = $_.Length
    $target = switch ($size) {
        {$_ -lt 100} { $dest1 }
        {$_ -ge 1000 -and $_ -lt 10000} { $dest2 }
        {$_ -ge 10000} { $dest3 }
        default { $null }
    }
    if ($target) {
        Copy-Item -Path $_.FullName -Destination $target -Force
    }
}

https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.5

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

Prog1
$options = @("Stein", "Schere", "Papier")
 
$playerChoice = Read-Host "Wähle Stein, Schere oder Papier"
 
if ($options -notcontains $playerChoice) {
    Write-Host "Ungültige Eingabe. Bitte Stein, Schere oder Papier eingeben."
    exit
}
 
$computerChoice = Get-Random -InputObject $options
Write-Host "Computer wählt: $computerChoice"
 
if ($playerChoice -eq $computerChoice) {
    Write-Host "Unentschieden!"
} elseif (($playerChoice -eq "Stein" -and $computerChoice -eq "Schere") -or
        ($playerChoice -eq "Schere" -and $computerChoice -eq "Papier") -or
        ($playerChoice -eq "Papier" -and $computerChoice -eq "Stein")) {
    Write-Host "Du gewinnst!"
} else {
    Write-Host "Computer gewinnt!"
}

Prog2
#Programm welches in jedem Unterordner die
#Dateien zählt die Unterordner sortiert und nach Anzahl
#der Dateien auflistet
 
 
 param(
    [string]$Path = "documents"   # Standardpfad (kann beim Start überschrieben werden)
)
# Prüfen, ob der Pfad existiert
if (-not (Test-Path $Path)) {
    Write-Error "Der Pfad '$Path' existiert nicht.    "  #Write-Error funktioniert nicht mit Farben
    return #Bei Powershell exit verwenden, bei Powershell ISE return sonst wird Powershell verlassen
}
 
# Alle Unterordner auswerten
$ordnerListe = Get-ChildItem -Path $Path -Directory | #listet Ordner im angegebenen Pfad auf
    ForEach-Object {
        [PSCustomObject]@{
            Ordner  = $_.Name
            Dateien = (Get-ChildItem -Path $_.FullName -File | Measure-Object).Count
        }
    } |
    Sort-Object Dateien -Descending   # Sortierung nach Anzahl Dateien
 
# Ergebnis als Tabelle anzeigen
$ordnerListe | Format-Table -AutoSize

Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

Pro3
# --- Teil 1: Ordner und Dateien vorbereiten ---
 
# Legt den Pfad in einer Variable ab
$ordnerPfad = "C:\TestOrdner"
 
# PRÜFUNG & BEREINIGUNG: Wenn der Ordner bereits existiert, wird er gelöscht.
if (Test-Path $ordnerPfad) {
    Write-Host "Bestehender Ordner '$ordnerPfad' wird für einen sauberen Start entfernt..." -ForegroundColor Yellow
    Remove-Item -Path $ordnerPfad -Recurse -Force
}
 
# Erstellt den Ordner neu
New-Item -Path $ordnerPfad -ItemType Directory
Write-Host "Ordner '$ordnerPfad' wurde erstellt." -ForegroundColor Green
 
# Erstellt die Beispieldateien (dies erzeugt jetzt keine Fehler mehr)
Write-Host "Erstelle Beispieldateien..."
fsutil file createnew "$ordnerPfad\GrosseDatei.zip" 25000000
fsutil file createnew "$ordnerPfad\MittlereDatei.txt" 5000000
fsutil file createnew "$ordnerPfad\KleineDatei.log" 800000
fsutil file createnew "$ordnerPfad\WinzigeDatei.dat" 15000
Write-Host "Beispieldateien wurden erstellt." -ForegroundColor Green
Write-Host "----------------------------------------------------"
 
 
 
Write-Host "Analysiere Dateien im Ordner '$ordnerPfad':"
Get-ChildItem -Path $ordnerPfad -File |
  Select-Object Name, @{Name="Größe (MB)"; Expression={[math]::Round($_.Length / 1MB, 2)}} |
  Sort-Object -Property "Größe (MB)" -Descending |
  Format-Table -AutoSize

  prog4
  Write-Host "Analysiere Dateien im Ordner '$ordnerPfad':"
Get-ChildItem -Path $ordnerPfad -File |
Select-Object Name, @{Name="Größe (MB)"; Expression={[math]:Round($ _. Length / 1MB, 2)33
Sort-Object -Property "Größe (MB)" -Descending I
Format-Table -AutoSize

prog5
# Eingabe vom Benutzer
$text = Read-Host "Gib einen Text ein, der in Binär konvertiert werden soll"
 
# Ausgabe-Überschrift
Write-Host "`nText in Binärdarstellung:`n"
 
# Jeden Buchstaben in Binär umwandeln
foreach ($char in $text.ToCharArray()) {
    $ascii = [int][char]$char
    $binary = [Convert]::ToString($ascii, 2).PadLeft(8, '0')
    Write-Host "$char`t= $binary"
}

prog6
https://open-meteo.com/en/docs/geocoding-api

clear # Konsole leeren
$stadt = read-host "Gib die Zielstadt ein" # Eingabe Zielstadt
$stadt = ($stadt.Substring(0,1).ToUpper() + $stadt.Substring(1).ToLower()) # 1. Buchstabe groß Rest klein
 
$geoUrl = "https://geocoding-api.open-meteo.com/v1/search?name=$stadt&count=1&language=de&format=json%22 # URL um Geokoordinaten zu ermitteln
$geoAnfrage = Invoke-RestMethod -Uri $geoUrl -Method Get # Anfrage an die API der Website um eine Antwort im Array $geoAnfrage  zu speichern
 
if (-not $geoAnfrage.results) { # Fehlerbehandlung wenn keine Koordinaten zu ermitteln sind
        Write-Host "Keine Koordinaten für '$city' gefunden."
        return # Programabruch
}
# $geoAnfrage.results
# aus der Antwort werden die Koordinaten entnommen
 
$breite = $geoAnfrage.results[0].latitude # im Array .latitute suchen und das Ergebnis in $breite speichern
$laenge = $geoAnfrage.results[0].longitude # im Array .longitute suchen und das Ergebnis in $laenge speichern
 
 
$wetterUrl = "https://api.open-meteo.com/v1/forecast?latitude=$breite&longitude=$laenge&current_weather=true&temperature_unit=celsius%22 # wetterurl 
try { # Fehlerbehandlung
    $wetterAnfrage = Invoke-RestMethod -Uri $wetterUrl -Method Get # Invoke-Methode um Anfrage an die URL senden. -Methode get fragt daten von der API ab
    $temp = $wetterAnfrage.current_weather.temperature # Temperaturdaten aus der rückgegebenen Antwort in Variable schreiben
    Write-Host "Aktuelle Temperatur in ${stadt}: ${temp}°C" # Ausgabe der empfangenen Daten auf der Konsole
} catch {
    Write-Host "Fehler beim Abrufen der Daten aus der Wetter-URL." # Ausgabe wenn Fehler auftritt
}

# Find-DuplicateImages.ps1
# Sucht nach doppelten Bildern anhand:
#   1) SHA256-Hash (exakte Kopie)
#   2) EXIF-Metadaten (Datum/Kamera/Größe)
# Gefundene Duplikate werden nach $Target verschoben
# ==============================
 
 
$Source = "C:\Users\Schulung\Desktop\TQ3\Powershell\Bilder"          # Ordner mit allen Bildern
$Target = "C:\Users\Schulung\Desktop\TQ3\Powershell\Bilderdoppelt" # Zielordner für Duplikate
$Extensions = ".jpg",".jpeg",".png",".tif",".tiff",".heic",".png"
 
# Zielordner erstellen, falls nicht vorhanden
if (-not (Test-Path $Target)) {
    New-Item -ItemType Directory -Path $Target | Out-Null
}
 
# Funktion: SHA256-Hash berechnen
function Get-FileHashString($Path) {
    return (Get-FileHash -Algorithm SHA256 -Path $Path).Hash
}
 
# Funktion: EXIF-Datum & Kamera auslesen
function Get-ImageMeta($Path) {
    try {
        $img = [System.Drawing.Image]::FromFile($Path)
        $props = $img.PropertyItems
        $dateTaken = ($props | Where-Object { $_.Id -eq 0x9003 }).Value
        $camera    = ($props | Where-Object { $_.Id -eq 0x0110 }).Value
        $size      = "$($img.Width)x$($img.Height)"
        $img.Dispose()
        # Byte-Array in String konvertieren
        $toString = { param($b) -join ([System.Text.Encoding]::ASCII.GetString($b) -split "`0") }
        return "$(($toString.Invoke($dateTaken))).$(($toString.Invoke($camera))).$size"
    }
    catch {
        return ""
    }
}
 
Write-Host ">>> Scanne Bilder im Ordner: $Source`n"
 
$files = Get-ChildItem -Path $Source -Recurse -File | 
         Where-Object { $Extensions -contains $_.Extension.ToLower() }
 
# Dictionaries für Vergleiche
$hashMap = @{}
$metaMap = @{}
 
foreach ($f in $files) {
    Write-Host "Prüfe: $($f.FullName)" -ForegroundColor DarkGray
    try {
        # 1) Hash prüfen
        $hash = Get-FileHashString $f.FullName
        if ($hashMap.ContainsKey($hash)) {
            # exakte Duplikate
            Move-Item -LiteralPath $f.FullName -Destination $Target -Force
            Write-Host "Duplikat (Hash): $($f.Name) → $Target" -ForegroundColor Yellow
            continue
        }
        else {
            $hashMap[$hash] = $f.FullName
        }
 
        # 2) EXIF-Metadaten prüfen
        $meta = Get-ImageMeta $f.FullName
        if ($meta -and $metaMap.ContainsKey($meta)) {
            Move-Item -LiteralPath $f.FullName -Destination $Target -Force
            Write-Host "Duplikat (EXIF): $($f.Name) → $Target" -ForegroundColor Cyan
        }
        else {
            if ($meta) { $metaMap[$meta] = $f.FullName }
        }
    }
    catch {
        Write-Host "Fehler bei: $($f.FullName)" -ForegroundColor Red
    }
}
 
Write-Host "`n>>> Fertig. Duplikate wurden nach $Target verschoben." -ForegroundColor Green
    }

prog 1x
    # Pfad zum Downloads-Ordner
$downloadsPath = [Environment]::GetFolderPath("UserProfile") + "\Downloads"
 
# Alle Dateien im Ordner
$allFiles = Get-ChildItem -Path $downloadsPath -File
 
# Gesamtanzahl aller Dateien
$totalCount = $allFiles.Count
 
# Alle Dateien mit W/w zählen
$wCount = ($allFiles | Where-Object {$_.Name.StartsWith('w') -or $_.Name.StartsWith('W') }).Count
 
# Dateien mit W/w UND Größe 100–1000 KB werden auch ausgegeben
$filteredFiles = $allFiles |
    Where-Object {$_.Name.StartsWith('w') -or $_.Name.StartsWith('W') } |
    Where-Object { $_.Length -ge 100KB -and $_.Length -le 1000KB } |
    Sort-Object Length, Name
 
# Ausgabe der gefilterten Dateien (Größe in KB und Name)
foreach ($file in $filteredFiles) {
   "{0:N0} KB  {1}" -f ($file.Length / 1KB), $file.Name
}
 
# Ausgabe
Write-Host ""
Write-Host "Anzahl aller Dateien im Downloads-Ordner: $totalCount"
Write-Host "Anzahl aller Dateien mit 'W' oder 'w': $wCount"
Write-Host "Anzahl der Dateien mit 'W' oder 'w' und Größe 100–1000 KB: $($filteredFiles.Count)"

----
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
----

prog2x
function Get-BiggestFile
{
    param(
        $root = ".",
        [int]$anzahl = 1,
        [switch]$Recurse
    )
 
    if($Recurse)
    {
        Write-Host "Es werden die Unterverzeichnisse von $root mit untersucht..."
    }
 
    $files = get-childitem -path $root -file -ErrorAction SilentlyContinue -Recurse:$Recurse

 
    $top = $files | 
        sort-object length -descending |
        select-object -first $anzahl FullName, @{Name="Größe(MB)";Expression={"{0:N2}" -f ($_.Length / 1MB)}}
 
    $top | Format-Table -AutoSize
}



