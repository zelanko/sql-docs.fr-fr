---
title: Aide (F1) de la visionneuse du profil des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d541e0c6143c9652629f80d911bf42db26e9a4ef
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429716"
---
# <a name="data-profile-viewer-f1-help"></a>Aide F1 de la Visionneuse du profil des données
  Utilisez la Visionneuse du profil des données pour afficher la sortie de la tâche de profilage des données.  
  
 Pour plus d’informations sur le mode d’utilisation de la Visionneuse du profil des données, consultez [Visionneuse du profil des données](control-flow/data-profile-viewer.md). Pour plus d’informations sur l’utilisation de la tâche de profilage des données, qui crée la sortie de profil que vous analysez dans la Visionneuse du profil des données, consultez [Configuration de la tâche de profilage des données](control-flow/data-profiling-task.md).  
  
## <a name="static-options"></a>Options statiques  
 **Ouvrir**  
 Cliquez pour accéder au fichier enregistré qui contient la sortie de la tâche de profilage des données.  
  
 Volet**Profils**  
 Développez l’arborescence du volet **Profils** pour consulter les profils inclus dans la sortie. Sélectionnez un profil afin d'afficher les résultats de ce profil.  
  
 Volet**Message**  
 Affiche des messages d'état.  
  
 Volet**Exploration vers le bas**  
 Affiche les lignes de données qui correspondent à une valeur dans la sortie, si la source de données utilisée par la tâche de profilage des données est disponible.  
  
 Par exemple, si vous affichez la sortie d’un profil de distribution de valeurs de colonne pour une colonne des états américains, le volet **Distribution de valeurs** peut contenir une ligne pour « WA ». Double-cliquez sur la ligne dans le volet **Distribution de valeurs** pour consulter les lignes de données pour lesquelles la valeur de la colonne d’état est « WA » dans le volet d’exploration.  
  
## <a name="dynamic-options"></a>Options dynamiques  
  
### <a name="profile-type--column-length-distribution-profile"></a>Type de profil = Profil de distribution de longueurs de colonne  
  
#### <a name="column-length-distribution-profile---column-pane"></a>Profil de distribution de longueurs de colonne- \<column> volet  
 **Longueur minimale**  
 Affiche la longueur minimale des valeurs de cette colonne.  
  
 **Longueur maximale**  
 Affiche la longueur maximale des valeurs de cette colonne.  
  
 **Ignorer les espaces de début**  
 Indique si ce profil a été calculé avec une valeur `IgnoreLeadingSpaces` True ou False. Cette propriété a été définie dans la page **Demandes de profil** de l’éditeur de tâche de profilage de données.  
  
 **Ignorez les espaces de fin**  
 Indique si ce profil a été calculé avec une valeur `IgnoreTrailingSpaces` True ou False. Cette propriété a été définie dans la page **Demandes de profil** de l’éditeur de tâche de profilage de données.  
  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
#### <a name="detailed-length-distribution-pane"></a>Volet de distribution de longueurs détaillé  
 **Longueur**  
 Affiche les longueurs de colonne trouvées dans la colonne profilée.  
  
 **Count**  
 Affiche le nombre de lignes dans lesquelles la valeur de la colonne profilée a la longueur affichée dans la colonne **Longueur** .  
  
 **Pourcentage**  
 Affiche le pourcentage de lignes dans lesquelles la valeur de la colonne profilée a la longueur affichée dans la colonne **Longueur** .  
  
### <a name="profile-type--column-null-ratio-profile"></a>Type de profil = Profil de ratio de colonne Null  
  
#### <a name="column-null-ratio-profile---column-pane"></a>Profil de ratio de colonne null- \<column> volet  
 **Nombre null**  
 Affiche le nombre de lignes dans lesquelles la colonne profilée possède une valeur NULL.  
  
 **Pourcentage null**  
 Affiche le pourcentage de lignes dans lesquelles la colonne profilée possède une valeur NULL.  
  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
### <a name="profile-type--column-pattern-profile"></a>Type de profil = Profil de modèle de colonne  
  
#### <a name="column-pattern-profile---column-pane"></a>Profil de motif de colonne- \<column> volet  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
#### <a name="pattern-distribution-pane"></a>Volet Distribution de modèles  
 **Modèle**  
 Affiche les modèles calculés pour la colonne profilée.  
  
 **Pourcentage**  
 Affiche le pourcentage de lignes dont les valeurs correspondent au modèle affiché dans la colonne **Modèle** .  
  
### <a name="profile-type--column-statistics-profile"></a>Type de profil = Profil de statistiques de colonnes  
  
#### <a name="column-statistics-profile---column-pane"></a>Profil de statistiques de colonnes- \<column> volet  
 **Minimum**  
 Affiche la valeur minimale trouvée dans la colonne profilée.  
  
 **Maximum**  
 Affiche la valeur maximale trouvée dans la colonne profilée.  
  
 **Interprété**  
 Affiche la moyenne des valeurs trouvées dans la colonne profilée.  
  
 **Écart type**  
 Affiche l'écart type des valeurs trouvées dans la colonne profilée.  
  
### <a name="profile-type--column-value-distribution-profile"></a>Type de profil = Profil de distribution de valeurs de colonne  
  
#### <a name="column-value-distribution-profile---column-pane"></a>Profil de distribution de valeurs de colonne- \<column> volet  
 **Nombre de valeurs distinctes**  
 Affiche le nombre de valeurs distinctes trouvées dans la colonne profilée.  
  
 **Nombre de lignes**  
 Affiche le nombre de lignes présentes dans la table ou la vue.  
  
#### <a name="detailed-value-distribution-pane"></a>Volet de distribution de valeurs détaillé  
 **Valeur**  
 Affiche les valeurs distinctes trouvées dans la colonne profilée.  
  
 **Count**  
 Affiche le nombre de lignes dans lesquelles la colonne profilée a la valeur affichée dans la colonne **Valeur** .  
  
 **Pourcentage**  
 Affiche le pourcentage de lignes dans lesquelles la colonne profilée a la valeur affichée dans la colonne **Valeur** .  
  
### <a name="profile-type--candidate-key-profile"></a>Type de profil = Profil de clé candidate  
  
#### <a name="candidate-key-profile---table-pane"></a>Profil de clé candidate- \<table> volet  
 **Colonnes clés**  
 Affiche les colonnes sélectionnées pour le profilage en tant que clé candidate.  
  
 **Puissance de la clé**  
 Affiche la puissance (sous forme de pourcentage) de la colonne ou de la combinaison de colonnes clés candidates. Une puissance de clé inférieure à 100 % indique qu'il existe des valeurs dupliquées.  
  
#### <a name="key-violations-pane"></a>Volet Violations de clé  
 **\<column1>, \<column2> , etc.**  
 Affiche les valeurs dupliquées qui ont été détectées dans la colonne profilée.  
  
 **Count**  
 Affiche le nombre de lignes dans lesquelles la colonne spécifiée possède la valeur affichée dans la première colonne.  
  
### <a name="profile-type--functional-dependency-profile"></a>Type de profil = Profil de dépendance fonctionnelle  
  
#### <a name="functional-dependency-profile-pane"></a>Volet Profil de dépendance fonctionnelle  
 **Colonnes déterminantes**  
 Affiche les colonnes sélectionnées comme colonnes déterminantes. Dans l'exemple où le même code postal américain doit systématiquement posséder le même état, le code postal est la colonne déterminante.  
  
 **Colonnes dépendantes**  
 Affiche les colonnes sélectionnées comme colonnes dépendantes. Dans l'exemple où le même code postal d'état américain doit systématiquement posséder le même état, l'état est la colonne déterminante.  
  
 **Puissance de la dépendance fonctionnelle**  
 Affiche la puissance (sous forme de pourcentage) de la dépendance fonctionnelle entre les colonnes. Une puissance de clé inférieure à 100% indique qu'il existe des situations où la valeur déterminante ne détermine pas la valeur dépendante. Dans l'exemple où le même code postal d'état américain doit systématiquement posséder le même état, cela indique probablement que certaines valeurs d'état ne sont pas valides.  
  
#### <a name="functional-dependency-violations-pane"></a>Volet Violations de la dépendance fonctionnelle  
  
> [!NOTE]  
>  Un pourcentage élevé de valeurs erronées dans les données peut générer des résultats inattendus d'un profil de dépendance fonctionnelle. Par exemple, 90 % des lignes ont une valeur État de « WI » pour une valeur Code postal de « 98052 ». Le profil signale les lignes qui contiennent la valeur d'état correcte de « WA » en tant que violations.  
  
 **\<determinant column name>**  
 Affiche la valeur de la colonne déterminante ou de la combinaison de colonnes dans cette instance d'une violation de dépendance fonctionnelle.  
  
 **\<dependent column name>**  
 Affiche la valeur de la colonne dépendante dans cette instance d'une violation de dépendance fonctionnelle.  
  
 **Nombre de supports**  
 Affiche le nombre de lignes dans lesquelles la valeur de colonne déterminante détermine la colonne dépendante.  
  
 **Nombre de violations**  
 Affiche le nombre de lignes dans lesquelles la valeur de colonne déterminante ne détermine pas la colonne dépendante. (Il s’agit des lignes dans lesquelles la valeur dépendante est la valeur affichée dans la **\<dependent column name>** colonne.)  
  
 **Pourcentage de supports**  
 Affiche le pourcentage de lignes dans lesquelles la colonne déterminante détermine la colonne dépendante.  
  
### <a name="profile-type--value-inclusion-profile"></a>Type de profil = Profil d'inclusion de valeur  
  
#### <a name="value-inclusion-profile-pane"></a>Volet du profil d'inclusion de valeur  
 **Colonnes côté sous-ensemble**  
 Affiche la colonne ou la combinaison de colonnes qui ont été profilées pour déterminer si elles figurent dans les colonnes du sur-ensemble.  
  
 **Colonnes côté sur-ensemble**  
 Affiche la colonne ou la combinaison de colonnes qui ont été profilées pour déterminer si elles incluent les valeurs dans les colonnes du sous-ensemble.  
  
 **Puissance d'inclusion**  
 Affiche la puissance (sous forme de pourcentage) du chevauchement entre les colonnes. Une puissance de clé inférieure à 100 % indique que dans certains cas, la valeur du sous-ensemble est introuvable parmi les valeurs du sur-ensemble.  
  
#### <a name="inclusion-violations-pane"></a>Volet des violations d'inclusion  
 **\<column1>, \<column2> , etc.**  
 Affiche les valeurs de la colonne ou des colonnes du sous-ensemble qui étaient introuvables dans la colonne ou les colonnes du sur-ensemble.  
  
 **Count**  
 Affiche le nombre de lignes dans lesquelles la colonne spécifiée possède la valeur affichée dans la première colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Visionneuse du profil des données](control-flow/data-profile-viewer.md)   
 [Tâche de profilage des données et visionneuse](control-flow/data-profiling-task-and-viewer.md)  
  
  
