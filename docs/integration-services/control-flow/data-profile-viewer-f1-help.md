---
title: "Aide&#160;F1 de la Visionneuse du profil des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "sql13.dts.dataprofileviewer.f1"
helpviewer_keywords: 
  - "visionneuse du profil des données [Integration Services]"
  - "tâche de profilage des données [Integration Services], visionneuse"
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Aide&#160;F1 de la Visionneuse du profil des donn&#233;es
  Utilisez la Visionneuse du profil des données pour afficher la sortie de la tâche de profilage des données.  
  
 Pour plus d’informations sur le mode d’utilisation de la Visionneuse du profil des données, consultez [Visionneuse du profil des données](../../integration-services/control-flow/data-profile-viewer.md). Pour plus d’informations sur l’utilisation de la tâche de profilage des données, qui crée la sortie de profil que vous analysez dans la Visionneuse du profil des données, consultez [Configuration de la tâche de profilage des données](../../integration-services/control-flow/setup-of-the-data-profiling-task.md).  
  
## Options statiques  
 **Ouvrir**  
 Cliquez pour accéder au fichier enregistré qui contient la sortie de la tâche de profilage des données.  
  
 Volet **Profils**  
 Développez l’arborescence du volet **Profils** pour consulter les profils inclus dans la sortie. Sélectionnez un profil afin d'afficher les résultats de ce profil.  
  
 Volet **Message**  
 Affiche des messages d'état.  
  
 Volet **Exploration vers le bas**  
 Affiche les lignes de données qui correspondent à une valeur dans la sortie, si la source de données utilisée par la tâche de profilage des données est disponible.  
  
 Par exemple, si vous affichez la sortie d’un profil de distribution de valeurs de colonne pour une colonne des états américains, le volet **Distribution de valeurs** peut contenir une ligne pour « WA ». Double-cliquez sur la ligne dans le volet **Distribution de valeurs** pour consulter les lignes de données pour lesquelles la valeur de la colonne d’état est « WA » dans le volet d’exploration.  
  
## Options dynamiques  
  
### Type de profil = Profil de distribution de longueurs de colonne  
  
#### Profil de distribution de longueurs de colonne - volet \<colonne>  
 **Longueur minimale**  
 Affiche la longueur minimale des valeurs de cette colonne.  
  
 **Longueur maximale**  
 Affiche la longueur maximale des valeurs de cette colonne.  
  
 **Ignorer les espaces de début**  
 Indique si ce profil a été calculé avec une valeur **IgnoreLeadingSpaces** True ou False. Cette propriété a été définie dans la page **Demandes de profil** de l’éditeur de tâche de profilage de données.  
  
 **Ignorez les espaces de fin**  
 Indique si ce profil a été calculé avec une valeur **IgnoreTrailingSpaces** True ou False. Cette propriété a été définie dans la page **Demandes de profil** de l’éditeur de tâche de profilage de données.  
  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
#### Volet de distribution de longueurs détaillé  
 **Longueur**  
 Affiche les longueurs de colonne trouvées dans la colonne profilée.  
  
 **Compter**  
 Affiche le nombre de lignes dans lesquelles la valeur de la colonne profilée a la longueur affichée dans la colonne **Longueur**.  
  
 **Pourcentage**  
 Affiche le pourcentage de lignes dans lesquelles la valeur de la colonne profilée a la longueur affichée dans la colonne **Longueur**.  
  
### Type de profil = Profil de ratio de colonne Null  
  
#### Profil de ratio de colonne Null - volet de \<colonne>  
 **Nombre null**  
 Affiche le nombre de lignes dans lesquelles la colonne profilée possède une valeur NULL.  
  
 **Pourcentage null**  
 Affiche le pourcentage de lignes dans lesquelles la colonne profilée possède une valeur NULL.  
  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
### Type de profil = Profil de modèle de colonne  
  
#### Profil de modèle de colonne - volet de \<colonne>  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
#### Volet Distribution de modèles  
 **Motif**  
 Affiche les modèles calculés pour la colonne profilée.  
  
 **Pourcentage**  
 Affiche le pourcentage de lignes dont les valeurs correspondent au modèle affiché dans la colonne **Modèle**.  
  
### Type de profil = Profil de statistiques de colonnes  
  
#### Profil de statistiques de colonnes - volet de \<colonne>  
 **Minimum**  
 Affiche la valeur minimale trouvée dans la colonne profilée.  
  
 **Maximum**  
 Affiche la valeur maximale trouvée dans la colonne profilée.  
  
 **Moyenne**  
 Affiche la moyenne des valeurs trouvées dans la colonne profilée.  
  
 **Écart type**  
 Affiche l'écart type des valeurs trouvées dans la colonne profilée.  
  
### Type de profil = Profil de distribution de valeurs de colonne  
  
#### Profil de distribution de valeurs de colonne - volet de \<colonne>  
 **Nombre de valeurs distinctes**  
 Affiche le nombre de valeurs distinctes trouvées dans la colonne profilée.  
  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
#### Volet de distribution de valeurs détaillé  
 **Value**  
 Affiche les valeurs distinctes trouvées dans la colonne profilée.  
  
 **Compter**  
 Affiche le nombre de lignes dans lesquelles la colonne profilée a la valeur affichée dans la colonne **Valeur**.  
  
 **Pourcentage**  
 Affiche le pourcentage de lignes dans lesquelles la colonne profilée a la valeur affichée dans la colonne **Valeur**.  
  
### Type de profil = Profil de clé candidate  
  
#### Profil de clé candidate - volet de \<table>  
 **Colonnes clés**  
 Affiche les colonnes sélectionnées pour le profilage en tant que clé candidate.  
  
 **Puissance de la clé**  
 Affiche la puissance (sous forme de pourcentage) de la colonne ou de la combinaison de colonnes clés candidates. Une puissance de clé inférieure à 100 % indique qu'il existe des valeurs dupliquées.  
  
#### Volet Violations de clé  
 **\<colonne1>, \<colonne2>, etc.**  
 Affiche les valeurs dupliquées qui ont été détectées dans la colonne profilée.  
  
 **Compter**  
 Affiche le nombre de lignes dans lesquelles la colonne spécifiée possède la valeur affichée dans la première colonne.  
  
### Type de profil = Profil de dépendance fonctionnelle  
  
#### Volet Profil de dépendance fonctionnelle  
 **Colonnes déterminantes**  
 Affiche les colonnes sélectionnées comme colonnes déterminantes. Dans l'exemple où le même code postal américain doit systématiquement posséder le même état, le code postal est la colonne déterminante.  
  
 **Colonnes dépendantes**  
 Affiche les colonnes sélectionnées comme colonnes dépendantes. Dans l'exemple où le même code postal d'état américain doit systématiquement posséder le même état, l'état est la colonne déterminante.  
  
 **Puissance de la dépendance fonctionnelle**  
 Affiche la puissance (sous forme de pourcentage) de la dépendance fonctionnelle entre les colonnes. Une puissance de clé inférieure à 100% indique qu'il existe des situations où la valeur déterminante ne détermine pas la valeur dépendante. Dans l'exemple où le même code postal d'état américain doit systématiquement posséder le même état, cela indique probablement que certaines valeurs d'état ne sont pas valides.  
  
#### Volet Violations de la dépendance fonctionnelle  
  
> [!NOTE]  
>  Un pourcentage élevé de valeurs erronées dans les données peut générer des résultats inattendus d'un profil de dépendance fonctionnelle. Par exemple, 90 % des lignes ont une valeur État de « WI » pour une valeur Code postal de « 98052 ». Le profil signale les lignes qui contiennent la valeur d'état correcte de « WA » en tant que violations.  
  
 **\<nom de colonne déterminante>**  
 Affiche la valeur de la colonne déterminante ou de la combinaison de colonnes dans cette instance d'une violation de dépendance fonctionnelle.  
  
 **\<nom de colonne dépendante>**  
 Affiche la valeur de la colonne dépendante dans cette instance d'une violation de dépendance fonctionnelle.  
  
 **Nombre de supports**  
 Affiche le nombre de lignes dans lesquelles la valeur de colonne déterminante détermine la colonne dépendante.  
  
 **Nombre de violations**  
 Affiche le nombre de lignes dans lesquelles la valeur de colonne déterminante ne détermine pas la colonne dépendante. (Il s’agit des lignes dans lesquelles la valeur dépendante est la valeur affichée dans la colonne **\<nom de colonne dépendante>**.)  
  
 **Pourcentage de supports**  
 Affiche le pourcentage de lignes dans lesquelles la colonne déterminante détermine la colonne dépendante.  
  
### Type de profil = Profil d'inclusion de valeur  
  
#### Volet du profil d'inclusion de valeur  
 **Colonnes côté sous-ensemble**  
 Affiche la colonne ou la combinaison de colonnes qui ont été profilées pour déterminer si elles figurent dans les colonnes du sur-ensemble.  
  
 **Colonnes côté sur-ensemble**  
 Affiche la colonne ou la combinaison de colonnes qui ont été profilées pour déterminer si elles incluent les valeurs dans les colonnes du sous-ensemble.  
  
 **Puissance d'inclusion**  
 Affiche la puissance (sous forme de pourcentage) du chevauchement entre les colonnes. Une puissance de clé inférieure à 100 % indique que dans certains cas, la valeur du sous-ensemble est introuvable parmi les valeurs du sur-ensemble.  
  
#### Volet des violations d'inclusion  
 **\<colonne1>, \<colonne2>, etc.**  
 Affiche les valeurs de la colonne ou des colonnes du sous-ensemble qui étaient introuvables dans la colonne ou les colonnes du sur-ensemble.  
  
 **Compter**  
 Affiche le nombre de lignes dans lesquelles la colonne spécifiée possède la valeur affichée dans la première colonne.  
  
## Voir aussi  
 [Visionneuse du profil des données](../../integration-services/control-flow/data-profile-viewer.md)   
 [Tâche de profilage des données et visionneuse](../../integration-services/control-flow/data-profiling-task-and-viewer.md)  
  
  