---
title: Gestion des versions du projet expert
seo-title: Gestion des versions du projet expert
description: En savoir plus sur la gestion des versions du projet Maven.
seo-description: Suivez cette page pour en savoir plus sur la gestion des versions du projet Maven
translation-type: tm+mt
source-git-commit: f5ff89820eb843b35b617d300dbbc07f19ca2c17

---


# Gestion des versions du projet expert {#project-version}

## Présentation de la gestion des versions de projet expert {#understanding-project-version}

Pour les déploiements d’étape et de production, Cloud Manager génère une version incrémentée unique.

Cette version est affichée sur la page des détails d’exécution du pipeline ainsi que sur la page d’activité. Lorsqu’une compilation est exécutée, le projet Maven est mis à jour pour utiliser cette version et une balise est créée dans le référentiel git avec cette version comme nom.

Si la version originale du projet répond à certains critères, la version mise à jour du projet expert fusionne la version originale du projet et la version générée par Cloud Manager. La balise utilise toutefois toujours la version générée. Pour que cette fusion se produise, la version originale du projet doit être formée avec exactement trois segments de version, par exemple 1.0.0 ou 1.2.3, mais pas 1.0 ou 1, et la version originale ne doit pas se terminer par -SNAPSHOT.

Si la version d’origine ne répond pas à ces critères, la version générée sera ajoutée à la version d’origine en tant que segment de nouvelle version. La version générée sera également légèrement modifiée pour inclure un tri et une gestion corrects des versions. Par exemple, en supposant une version générée de 2019.926.121356.000020490 :

| **Version** | **version dans pom.xml** | **Commentaire** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Version originale correctement formée |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Version d’instantané, écrasée |
| 1 | 2019.926.121356.0000020490 | Version incomplète, écrasée |

>[!NOTE]
>
>Que la version d’origine ait été incorporée ou non dans la version initialisée de Cloud Manager, la version d’origine est disponible sous la forme d’une propriété Maven nommée *cloudManagerOriginalVersion.*
