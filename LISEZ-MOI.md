# Fongluciole : projet Forge 1.20.1 (prêt pour NYXO-jar, mode Auto)

Configuration réelle et cohérente (aucune métadonnée factice) :
- Minecraft **1.20.1** : `gradle.properties` (`minecraft_version`) et `mods.toml` (`[1.20.1,1.21)`)
- **Forge 47.2.0** (loader 47) : `gradle.properties`, `build.gradle` (plugin ForgeGradle 6) et `mods.toml` (`javafml`, `[47,)`)
- **Java 17** : `build.gradle` (`java.toolchain`)
- **Gradle 8.1.1** : `gradle/wrapper/gradle-wrapper.properties`
- Dépôt Maven de Forge pour le plugin : `settings.gradle`
- Identifiant du mod `fongluciole` : identique dans `@Mod`, `mods.toml`, `gradle.properties` et les dossiers `assets/` et `data/`

## Important : le wrapper est incomplet
Le fichier binaire `gradle/wrapper/gradle-wrapper.jar` et les scripts `gradlew` / `gradlew.bat` ne peuvent pas être
créés sans Gradle ; ils ne sont donc pas inclus (pas de faux fichiers). Pour un wrapper authentique : télécharge le MDK
Forge 1.20.1 et copie dans ce dossier `gradlew`, `gradlew.bat` et le dossier `gradle` (le jar y est), en remplaçant celui d'ici.

## Mémoire (OutOfMemoryError: Java heap space)
La partie la plus gourmande n'est pas ton mod (16 classes) mais ForgeGradle qui prépare Minecraft 1.20.1 (remappage, décompilation).
Options déjà économes dans `gradle.properties` : `-Xmx3G` (valeur du MDK, non augmentée), `-XX:+UseSerialGC`, une seule tâche à la fois.
`build.gradle` est allégé (plugins IDE retirés) et affiche « Heap max Gradle » pour voir la mémoire réellement allouée.

## Obtenir le .jar chez toi
Depuis ce dossier (celui qui contient `build.gradle`) : `gradlew.bat build` (avec le wrapper du MDK) ou `gradle build`.
Résultat : `build/libs/fongluciole-1.0.0.jar`. Ce projet n'a pas pu être compilé là où il a été écrit.
