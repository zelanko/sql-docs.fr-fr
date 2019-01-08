---
title: Génération de rapports (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: abb4264a-622e-4215-af5b-14e309b8a399
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fe6f45b2e35761fac5f8c49012b1eb370645bcb1
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52412766"
---
# <a name="generating-reports-accesstosql"></a>Génération de rapports (AccessToSQL)
Les rapports de certaines activités effectuées à l’aide des commandes sont générées dans la Console SSMA au niveau d’arborescence objet.  
  
Utilisez la procédure suivante pour générer des rapports :  
  
1.  Spécifiez le **écriture-résumé-rapports pour** paramètre. Le rapport est stocké en tant que le nom de fichier (si spécifié) ou dans le dossier que vous spécifiez. Le nom de fichier est prédéfinie par le système comme indiqué dans le tableau ci-dessous where, **&lt;n&gt;** est le nombre de fichiers uniques qui incrémente par un chiffre à chaque exécution de la même commande.  
  
    Les rapports à l’égard des commandes sont :  
  
    ||||  
    |-|-|-|  
    |**Sl. Non.**|**Commande**|**Titre de rapport**|  
    |1|Générer--rapport d’évaluation|AssessmentReport&lt;n&gt;. XML|  
    |2|convert-schema|SchemaConversionReport&lt;n&gt;.XML|  
    |3|migrer des données|DataMigrationReport&lt;n&gt;. XML|  
    |4|synchroniser la cible|TargetSynchronizationReport&lt;n&gt;.XML|  
    |5|actualisation de base de données|SourceDBRefreshReport&lt;n&gt;. XML|  
  
    > [!IMPORTANT]  
    > Un rapport de sortie est différent de rapport d’évaluation. Le premier est un rapport sur les performances d’une commande exécutée lors de la, ce dernier est un rapport XML pour la consommation par programmation.  
  
    Pour les options de commande pour les rapports de sortie (à partir de Sl. Non. 2 à 4 ci-dessus), reportez-vous à la [l’exécution de la Console SSMA &#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) section.  
  
2.  Indiquer l’étendue de détail souhaité dans le rapport de sortie en utilisant les paramètres de niveau de détail de rapport :  
  
    ||||  
    |-|-|-|  
    |**Sl. Non.**|**Commande et paramètre**|**Description de la sortie**|  
    |1|verbose = « false »|Génère un rapport de synthèse de l’activité.|  
    |2|verbose = « true »|Génère un rapport d’état résumées et détaillées pour chaque activité.|  
  
    > [!NOTE]  
    > Les paramètres de niveau de détail de rapport spécifié ci-dessus sont applicables pour générer--rapport d’évaluation, convert-schéma, les commandes de migrer des données.  
  
3.  Indiquer l’étendue de détail que vous souhaitez pour les rapports d’erreurs en utilisant les paramètres de rapport d’erreurs :  
  
    ||||  
    |-|-|-|  
    |**Sl. Non.**|**Commande et paramètre**|**Description de la sortie**|  
    |1|signaler les erreurs = « false »|Aucun détail d’erreur / avertissement / messages d’informations.|  
    |2|signaler les erreurs = « true »|Détails de l’erreur / avertissement / messages d’informations.|  
  
    > [!NOTE]  
    > Les paramètres de rapport d’erreurs spécifiées ci-dessus sont applicables pour générer--rapport d’évaluation, convert-schéma, les commandes de migrer des données.  
  
**Exemple :**  
  
```xml  
<generate-assessment-report  
  
    object-name="testschema"  
  
    object-type="Schemas"  
  
    verbose="yes"  
  
    report-erors="yes"  
  
    write-summary-report-to="$AssessmentFolder$\Report1.xml"  
  
    assessment-report-folder="$AssessmentFolder$\assesment_report"  
  
    assessment-report-overwrite="true"  
  
/>  
```  
  
### <a name="synchronize-target"></a>synchroniser-cible :  
La commande **cible synchroniser** a **erreurs de rapports pour** paramètre, qui spécifie l’emplacement du rapport d’erreurs pour l’opération de synchronisation. Ensuite, un fichier par nom **TargetSynchronizationReport&lt;n&gt;. XML** est créé à l’emplacement spécifié, où **&lt;n&gt;** est le nombre de fichiers uniques qui incrémente par un chiffre à chaque exécution de la même commande.  
  
**Remarque :** Si le chemin du dossier est indiqué, 'rapports erreurs-pour' paramètre devient un attribut facultatif pour la commande 'synchroniser-target'.  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="$TargetDB$.dbo"  
  
    on-error="fail-script"  
  
    report-errors-to="$SynchronizationReports$"  
  
/>  
```  
**nom de l’objet :** Spécifie l’ou les objets pris en compte pour la synchronisation (il peut également avoir des noms d’objets individuels ou un nom d’objet de groupe).  
  
**en cas d’erreur :** Spécifie s’il faut spécifier des erreurs de synchronisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
-   Rapport total en tant qu’avertissement  
  
-   rapport-each-sous-avertissement  
  
-   Échec-script  
  
### <a name="refresh-from-database"></a>actualisation-de-base de données :  
La commande **actualisation à partir de base de données** a **erreurs de rapports pour** paramètre, qui spécifie l’emplacement du rapport d’erreurs pour l’opération d’actualisation. Ensuite, un fichier par nom **SourceDBRefreshReport&lt;n&gt;. XML** est créé à l’emplacement spécifié, où **&lt;n&gt;** est le nombre de fichiers uniques qui incrémente par un chiffre à chaque exécution de la même commande.  
  
**Remarque :** Si le chemin du dossier est indiqué, 'rapports erreurs-pour' paramètre devient un attribut facultatif pour la commande 'synchroniser-target'.  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
    object-name="$SourceDatabaseStandard$"  
  
    object-type ="Databases"  
  
    on-error="fail-script"  
  
    report-errors-to="$RefreshDBFolder$\RefreshReport.xml"  
  
/>  
```  
**nom de l’objet :** Spécifie l’ou les objets pris en compte pour actualisation (il peut également avoir des noms d’objets individuels ou un nom d’objet de groupe).  
  
**en cas d’erreur :** Spécifie s’il faut spécifier des erreurs d’actualisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
-   Rapport total en tant qu’avertissement  
  
-   rapport-each-sous-avertissement  
  
-   Échec-script  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la Console SSMA (accès)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
