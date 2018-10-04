---
title: Profilage des données, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.f1
helpviewer_keywords:
- Data Profiling task [Integration Services], about Data Profiling task
- data profiling
- profiling data
ms.assetid: 248ce233-4342-42c5-bf26-f4387ea152cf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0ccb9267242dbe3a44350efd1762c45bc6bbccbf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140700"
---
# <a name="data-profiling-task"></a>Tâche de profilage des données
  La tâche de profilage des données calcule différents profils qui vous aident à vous familiariser avec une source de données et à identifier les problèmes à résoudre au niveau des données.  
  
 Vous pouvez utiliser la tâche de profilage des données à l’intérieur d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour profiler les données stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour identifier les problèmes potentiels de qualité des données.  
  
> [!NOTE]  
>  Cette rubrique décrit uniquement le les fonctionnalités et les spécifications de la tâche de profilage des données. Pour connaître la procédure pas à pas d’utilisation de la tâche de profilage des données, consultez la section [Tâche de profilage des données et visionneuse](data-profiling-task-and-viewer.md).  
  
## <a name="requirements-and-limitations"></a>Limitations et exigences  
 La tâche de profilage des données fonctionne uniquement avec les données stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette tâche ne fonctionne pas avec les sources de données tierces ou basées sur des fichiers.  
  
 En outre, pour exécuter un package qui contient la tâche de profilage des données, vous devez utiliser un compte qui dispose d'autorisations de lecture/écriture, notamment les autorisations CREATE TABLE, sur la base de données tempdb.  
  
## <a name="data-profiler-viewer"></a>Visionneuse du profil des données  
 Après avoir utilisé la tâche pour calculer des profils de données et enregistrer ceux-ci dans un fichier, vous pouvez utiliser la visionneuse du profil des données autonome pour passer en revue la sortie du profil. La visionneuse du profil des données prend également en charge l'exploration vers le bas pour vous aider à comprendre les problèmes de qualité des données qui sont identifiés dans la sortie du profil. Pour plus d’informations, consultez [Visionneuse du profil des données](data-profile-viewer.md).  
  
> [!IMPORTANT]  
>  Le fichier de sortie peut contenir des données sensibles qui concernent votre base de données et les données qu’elle contient. Pour obtenir des suggestions sur la manière de sécuriser davantage ce fichier, consultez [Accéder aux fichiers utilisés par des packages](../access-to-files-used-by-packages.md).  
>   
>  La fonction d'exploration vers le bas, disponible dans la visionneuse du profil des données, envoie des requêtes actives à la source de données d'origine.  
  
## <a name="available-profiles"></a>Profils disponibles  
 La tâche de profilage des données peut calculer huit profils de données différents. Cinq de ces profils analysent des colonnes individuelles, tandis que les trois autres analysent plusieurs colonnes ou les relations entre des colonnes et des tables.  
  
 Les cinq profils suivants analysent des colonnes individuelles.  
  
|Profils qui analysent des colonnes individuelles|Description|  
|----------------------------------------------|-----------------|  
|Profil de distribution de longueurs de colonne|Signale toutes les longueurs distinctes des valeurs de chaîne dans la colonne sélectionnée, ainsi que le pourcentage de lignes dans la table que chaque longueur représente.<br /><br /> Ce profil vous aide à identifier des problèmes dans vos données, tels que des valeurs non valides. Par exemple, vous profilez une colonne des codes des États américains, ceux-ci comportant deux caractères, et découvrez des valeurs excédant deux caractères.|  
|Profil de ratio de colonne Null|Signale le pourcentage de valeurs Null dans la colonne sélectionnée.<br /><br /> Ce profil vous aide à identifier des problèmes dans vos données, tels qu'un ratio élevé inattendu de valeurs Null dans une colonne. Par exemple, vous profilez une colonne de codes postaux et découvrez un pourcentage élevé et inacceptable de codes manquants.|  
|Profil de modèle de colonne|Signale un ensemble d'expressions régulières qui reflètent le pourcentage spécifié de valeurs dans une colonne de chaîne.<br /><br /> Ce profil vous aide à identifier des problèmes dans vos données, tels que des chaînes non valides. Il peut également suggérer des expressions régulières susceptibles d'être utilisées à l'avenir pour la validation de nouvelles valeurs. Par exemple, un profil de modèle d'une colonne de codes postaux américains peut générer les expressions régulières \d{5}-\d{4}, \d{5} et \d{9}. Si vous rencontrez d'autres expressions régulières, il est probable que vos données contiennent des valeurs qui ne sont pas valides ou utilisent un format incorrect.|  
|Profil de statistiques de colonnes|Fournit des statistiques, telles que le minimum, maximum, moyenne et écart type pour les colonnes numériques et au minimum et maximum pour `datetime` colonnes.<br /><br /> Ce profil vous aide à identifier des problèmes dans vos données, tels que des dates non valides. Par exemple, vous profilez une colonne de dates historiques et découvrez une date maximum dont l'échéance est à venir.|  
|Profil de distribution de valeurs de colonne|Signale toutes les valeurs distinctes dans la colonne sélectionnée, ainsi que le pourcentage de lignes dans la table que chaque valeur représente. Peut également signaler des valeurs qui représentent plus qu'un pourcentage de lignes spécifié dans la table.<br /><br /> Ce profil vous aide à identifier des problèmes dans vos données, tels qu'un nombre incorrect de valeurs distinctes dans une colonne. Par exemple, vous profilez une colonne supposée contenir les États américains et découvrez plus de 50 valeurs distinctes.|  
  
 Les trois profils suivants analysent plusieurs colonnes ou les relations entre des colonnes et des tables.  
  
|Profils qui analysent plusieurs colonnes|Description|  
|--------------------------------------------|-----------------|  
|Profil de clé candidate|Signale si une colonne ou un ensemble de colonnes est une clé, ou une clé approximative, pour la table sélectionnée.<br /><br /> Ce profil vous aide également à identifier des problèmes dans vos données, tels que des valeurs dupliquées dans une colonne clé potentielle.|  
|Profil de dépendance fonctionnelle|Signale le degré de dépendance entre les valeurs d'une colonne (colonne dépendante) et celles d'une autre colonne ou d'un ensemble de colonnes (colonne déterminante).<br /><br /> Ce profil vous aide également à identifier des problèmes dans vos données, tels que des valeurs non valides. Par exemple, vous profilez la dépendance entre une colonne qui contient les codes postaux américains et une colonne qui contient les États américains. Le même code postal doit toujours afficher le même état mais le profil détecte des violations de la dépendance.|  
|Profil d'inclusion de valeur|Calcule le chevauchement des valeurs entre deux colonnes ou ensembles de colonnes. Ce profil permet de déterminer si une colonne ou un ensemble de colonnes peut servir de clé étrangère entre les tables sélectionnées.<br /><br /> Ce profil vous aide également à identifier des problèmes dans vos données, tels que des valeurs non valides. Par exemple, vous profilez la colonne ProductID d'une table Sales et découvrez que la colonne contient des valeurs qui sont introuvables dans la colonne ProductID de la table Products.|  
  
## <a name="prerequisites-for-a-valid-profile"></a>Conditions requises pour obtenir un profil valide  
 Pour qu'un profil soit valide, vous devez sélectionner des tables et des colonnes qui ne sont pas vides, et les colonnes doivent contenir des types de données valides pour le profil.  
  
### <a name="valid-data-types"></a>Types de données valides  
 Certains des profils disponibles ne sont significatifs que pour certains types de données. Par exemple, le fait de calculer un profil de modèle de colonne pour une colonne qui contient des valeurs numériques ou `datetime` n'est pas significatif. Par conséquent, un tel profil n'est pas valide.  
  
|Profil|Types de données valides*|  
|-------------|------------------------|  
|ColumnStatisticsProfile|Colonnes de type numérique ou de type `datetime` (`mean` et `stddev` ne sont pas disponibles pour une colonne `datetime`)|  
|ColumnNullRatioProfile|Toutes les colonnes*|  
|ColumnValueDistributionProfile|Colonnes de `integer` type, `char` type, et `datetime` type|  
|ColumnLengthDistributionProfile|Colonnes de `char` type|  
|ColumnPatternProfile|Colonnes de `char` type|  
|CandidateKeyProfile|Colonnes de `integer` type, `char` type, et `datetime` type|  
|FunctionalDependencyProfile|Colonnes de `integer` type, `char` type, et `datetime` type|  
|InclusionProfile|Colonnes de `integer` type, `char` type, et `datetime` type|  
  
 \* Dans le tableau précédent des types de données valides, le `integer`, `char`, `datetime`, et `numeric` incluent les types de données spécifiques suivants :  
  
 Les types d'entiers sont `bit`, `tinyint`, `smallint`, `int` et `bigint`.  
  
 Les types de caractères incluent `char`, `nchar`, `varchar` et `nvarchar,`, mais pas `varchar(max)` et `nvarchar(max)`.  
  
 Les types de date et d'heure incluent `datetime`, `smalldatetime` et `timestamp`.  
  
 Types numériques incluent `integer` types (à l’exception `bit`), `money`, `smallmoney`, `decimal`, `float`, `real`, et `numeric`.  
  
 \*\* `image`, `text`, `XML`, `udt`, et `variant` types ne sont pas pris en charge pour les profils autre que le profil de Ratio Null de colonne.  
  
### <a name="valid-tables-and-columns"></a>Tables et colonnes valides  
 Si la table ou colonne est vide, la tâche de profilage des données entreprend les actions suivantes :  
  
-   Lorsque la table ou la vue sélectionnée est vide, la tâche de profilage des données ne calcule pas de profils.  
  
-   Lorsque toutes les valeurs dans la colonne sélectionnée sont Null, la tâche de profilage des données calcule uniquement le profil de ratio de colonne Null. La tâche ne calcule pas les profils de distribution de longueurs de colonne, de modèle de colonne, de statistiques de colonnes ou de distribution de valeurs de colonne.  
  
## <a name="features-of-the-data-profiling-task"></a>Fonctionnalités de la tâche de profilage des données  
 Pratiques, les options de configuration de la tâche de profilage des données sont les suivantes :  
  
-   **Colonnes génériques** Quand vous configurez une demande de profil, la tâche accepte le caractère générique **(\*)** à la place d’un nom de colonne. Cela simplifie la configuration et facilite la découverte des caractéristiques de données inconnues. Lorsque la tâche s'exécute, elle profile chaque colonne ayant un type de données approprié.  
  
-   **Profil rapide** Vous pouvez sélectionner Profil rapide pour configurer la tâche rapidement. Un profil rapide profile une table ou une vue en utilisant tous les profils et paramètres par défaut.  
  
## <a name="custom-logging-messages-available-on-the-data-profililng-task"></a>Messages de journalisation personnalisés disponibles dans la tâche de profilage des données  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de profilage des données. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|**DataProfilingTaskTrace**|Donne des informations détaillées sur l'état de la tâche. Les messages contiennent les informations suivantes :<br /><br /> Début de traitement des requêtes<br /><br /> Début de requête<br /><br /> Query End<br /><br /> Fin du calcul de requête|  
  
## <a name="output-and-its-schema"></a>Sortie et son schéma  
 La tâche de profilage des données génère en sortie les profils sélectionnés en langage XML structuré conformément au schéma DataProfile.xsd. Vous pouvez préciser si cette sortie XML doit être enregistrée dans un fichier ou dans une variable de package. Vous pouvez voir ce schéma en ligne sur [http://schemas.microsoft.com/sqlserver/2008/DataDebugger/](http://schemas.microsoft.com/sqlserver/2008/DataDebugger/). Vous pouvez, à partir de la page web, enregistrer une copie locale du schéma. Vous pouvez ensuite afficher la copie locale du schéma dans Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou un autre éditeur de schéma, dans un éditeur XML ou encore dans un éditeur de texte tel que le Bloc-notes.  
  
 Ce schéma pour les informations sur la qualité des données peut être utile pour :  
  
-   échanger des informations sur la qualité des données au sein d'une organisation ou entre plusieurs organisations ;  
  
-   construire des outils personnalisés qui fonctionnent avec les informations sur la qualité des données.  
  
 L’espace de noms cible est identifié dans le schéma en tant que [http://schemas.microsoft.com/sqlserver/2008/DataDebugger/](http://schemas.microsoft.com/sqlserver/2008/DataDebugger/).  
  
## <a name="output-in-the-conditional-workflow-of-a-package"></a>Sortie dans le flux de travail conditionnel d'un package  
 Les composants de profilage des données n'incluent pas de fonctionnalités intégrées pour implémenter la logique conditionnelle dans le flux de travail du package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] basée sur la sortie de la tâche de profilage des données. Toutefois, vous pouvez ajouter facilement cette logique, avec un minimum de programmation, dans une tâche de script. Ce code effectuerait une requête XPath sur la sortie XML, puis enregistrerait le résultat dans une variable de package. Les contraintes de précédence qui connectent la tâche de script aux tâches suivantes peuvent utiliser une expression pour déterminer le flux de travail. Par exemple, la tâche de script détecte que le pourcentage de valeurs Null dans une colonne dépasse un certain seuil. Lorsque cette condition est remplie, vous pouvez interrompre le package et résoudre le problème avant de continuer.  
  
## <a name="configuration-of-the-data-profiling-task"></a>Configuration de la tâche de profilage des données  
 Vous configurez la tâche de profilage des données en utilisant **l’Éditeur de tâche de profilage de données**. L'éditeur comprend deux pages :  
  
 [Page Général](../general-page-of-integration-services-designers-options.md)  
 Dans la page **Général** , vous spécifiez le fichier ou la variable de sortie. Vous pouvez également sélectionner **Profil rapide** pour configurer rapidement la tâche afin de calculer des profils à l’aide des paramètres par défaut. Pour plus d’informations, consultez [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](data-profiling-task.md).  
  
 [Page demandes de profil](data-profiling-task-editor-profile-requests-page.md)  
 Dans la page **Demandes de profil** , vous spécifiez la source de données et vous sélectionnez et configurez les profils de données à calculer. Pour plus d'informations sur les différents profils que vous pouvez configurer, consultez les rubriques suivantes :  
  
-   [Options de demande de profil de clé candidate &#40;tâche de profilage des données&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Options de demande de profil de Distribution de longueurs de colonne &#40;tâche de profilage des données&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Options de demande de profil de Ratio Null de la colonne &#40;tâche de profilage des données&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Options de demande de profil de modèle de colonne &#40;tâche de profilage des données&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Options demande de profil de statistiques de colonnes &#40;tâche de profilage des données&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Options de demande de profil de Distribution de valeurs de colonne &#40;tâche de profilage des données&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Options de demande de profil de dépendance fonctionnelle &#40;tâche de profilage des données&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Options demande de profil d’Inclusion de valeur &#40;tâche de profilage des données&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
  
