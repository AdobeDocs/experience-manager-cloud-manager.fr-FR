---
title: Gestion des versions de projet par Maven
description: Découvrez comment Maven gère le contrôle de version des projets dans Cloud Manager.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '249'
ht-degree: 100%

---


# Gestion des versions de projet par Maven {#project-version}

Découvrez comment Maven gère le contrôle de version des projets dans Cloud Manager.

## Gestion des versions des projets par Maven {#how-maven}

Pour les déploiements d’évaluation et de production, Cloud Manager génère une version d’incrémentation unique.

Cette version est affichée sur la page des détails d’exécution du pipeline, ainsi que sur la page des activités. Lorsqu’une version est exécutée, le projet Maven est mis à jour pour utiliser cette version. Une balise est créée dans le référentiel Git avec cette version comme nom.

Si la version d’origine du projet répond à certains critères, la version mise à jour du projet Maven fusionne la version originale du projet et la version générée par Cloud Manager. Toutefois, la balise utilise toujours la version générée. Pour que cette fusion s’effectue, la version initiale du projet doit être formée avec exactement trois segments de version, comme `1.0.0` ou `1.2.3`, mais pas `1.0` ou `1`. Par ailleurs, la version initiale ne doit pas se terminer par `-SNAPSHOT`.

>[!NOTE]
>
>Cette valeur de version de projet d’origine doit être définie de manière statique dans l’élément `<version>` du fichier `pom.xml` de niveau supérieur dans la branche du référentiel Git.

Si la version d’origine ne répond pas à ces critères, la version générée est ajoutée à la version d’origine en tant que segment de nouvelle version. La version générée est également légèrement modifiée pour inclure un tri et une gestion corrects des versions. Par exemple, en supposant une version générée de `2019.926.121356.0000020490` :

| Version | Version dans `pom.xml` | Commentaire |
| --- | --- | --- |
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Version originale correctement formée |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Version Snapshot, écrasée |
| `1` | `2019.926.121356.0000020490` | Version incomplète, écrasée |

>[!NOTE]
>
>Que la version d’origine ait été intégrée ou non à la version initialisée de Cloud Manager, elle est toujours accessible sous la forme de propriété Maven nommée `cloudManagerOriginalVersion`.
