
# LeetSpeak Encoder/Decoder

Ce script Python permet d'encoder ou de décoder des fichiers texte en utilisant le langage LeetSpeak. Il prend en charge à la fois la conversion de texte normal en LeetSpeak et la conversion inverse de LeetSpeak vers du texte lisible. Si vous codez en LeetSpeak avec vos propres codes, vous pouvez modifier le dictionnaire qui se trouve au début du fichier script.py.

Le script utilise la bibliothèque `argparse` pour gérer les arguments en ligne de commande, permettant ainsi une utilisation flexible et intuitive.

## Fonctionnalités

- **Encodage en LeetSpeak** : Convertit du texte normal en LeetSpeak.
- **Décodage depuis LeetSpeak** : Convertit un fichier LeetSpeak en texte normal.
- **Remplacement du fichier d'origine** : Si aucun fichier de sortie n'est spécifié, le fichier d'entrée sera remplacé par le fichier encodé/décodé, avec un changement d'extension approprié.
- **Fichier de sortie personnalisé** : Si un fichier de sortie est spécifié avec l'option `-o`, le résultat sera enregistré sous ce nom.
- **Mode d'opération configurable** : Permet de spécifier si l'on souhaite encoder ou décoder le fichier en utilisant l'option `--mode` (`encode` par défaut).

## Installation

1. Clonez le dépôt GitHub.
2. Accédez au dossier du projet depuis votre terminal.
3. Exécutez le script avec Python (version 3.6 ou supérieure est recommandée).

## Utilisation

### Syntaxe

```bash
python script.py <nom_du_fichier> [--mode {encode,decode}] [-o <fichier_de_sortie>]
```

### Arguments

- `nom_du_fichier` : Le fichier texte à encoder ou décoder.
- `--mode` : Mode d'opération, `encode` pour encoder en LeetSpeak (par défaut), `decode` pour décoder un fichier LeetSpeak.
- `-o <fichier_de_sortie>` : Nom du fichier de sortie. Si omis, le fichier d'entrée est remplacé avec un changement d'extension approprié (`.leet` pour l'encodage et `.txt` pour le décodage).

### Exemples

#### Encodage d'un fichier en LeetSpeak et remplacement de l'original

Si vous ne spécifiez pas d'option de sortie, le fichier original sera remplacé, et son extension sera modifiée en `.leet`.

```bash
python script.py input.txt --mode encode
```

Ce qui remplacera `input.txt` par `input.leet`.

#### Décodage d'un fichier LeetSpeak en texte normal

Le fichier `.leet` sera décodé en texte et sauvegardé avec une extension `.txt`.

```bash
python script.py input.leet --mode decode
```

Cela remplacera `input.leet` par `input.txt`.

#### Encodage avec un fichier de sortie spécifié

Vous pouvez aussi encoder un fichier en LeetSpeak et sauvegarder le résultat dans un fichier différent :

```bash
python script.py input.txt --mode encode -o output.leet
```

Le résultat sera écrit dans `output.leet`.

### Afficher l'aide

Pour obtenir une aide sur l'utilisation du script et les options disponibles, utilisez l'option `--help` :

```bash
python script.py --help
```

Cela affichera l'aide suivante :

```
usage: script.py [-h] [-m {encode,decode}] [-o OUTPUT] filename

Encoder ou décoder un fichier en LeetSpeak.

positional arguments:
  filename              Nom du fichier à traiter.

optional arguments:
  -h, --help            show this help message and exit
  -m {encode,decode}, --mode {encode,decode}
                        Mode d'opération : encode ou decode.
  -o OUTPUT, --output OUTPUT
                        Nom du fichier de sortie (avec extension).
```

## Détails Techniques

Le script utilise deux dictionnaires pour la conversion entre le texte normal et LeetSpeak :

- Un dictionnaire `leetspeak` pour encoder chaque lettre en LeetSpeak.
- Un dictionnaire inversé `leetspeak_inv` pour décoder chaque séquence LeetSpeak vers la lettre correspondante.

La conversion est effectuée de manière simple en parcourant chaque ligne du fichier d'entrée, puis en appliquant les transformations.
