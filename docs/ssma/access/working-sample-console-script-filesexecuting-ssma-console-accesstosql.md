---
title: Utiliser la Console SSMA exemple Console Script FilesExecuting | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ad75b648-d119-4119-98f0-d18f058be68d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d6fea9a78928e2944cba1571737008965d679759
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938385"
---
# <a name="working-with-the-sample-console-script-filesexecuting-the-ssma-console-accesstosql"></a>Utilisation de la FilesExecuting de Script de Console exemple la Console SSMA (AccessToSQL)
Quelques exemples de fichiers ont été fournis, ainsi que le produit pour la référence de l’utilisateur et l’utilisation. Cette section décrit la façon de personnaliser facilement ces scripts en fonction des besoins des utilisateurs finaux.  
  
## <a name="sample-console-script-files"></a>Exemples de fichiers de Script Console  
Les fichiers de script de console exemple suivants couvrant différents scénarios ont été fournies pour la référence de l’utilisateur :  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   **ServersConnectionFileSample.xml :**  
  
    -   Cet exemple donne les différents modes de connexion disponible à la base de données source et cible et l’utilisateur peut sélectionner n’importe quel mode selon les besoins. Cet exemple contient les définitions de serveur.  
  
    -   L’utilisateur peut se connecter à la base de données requis en modifiant simplement les valeurs à la source requis et les définitions de serveur cible. Dans l’exemple fourni toutes les valeurs ont été fournies comme variable les valeurs qui sont disponibles dans le **VariableValueFileSample.xml**. Tous les autres paramètres de connexion peuvent être supprimés du fichier de connexion de serveur de travail de l’utilisateur.  
  
    -   Pour plus d’informations sur la connexion au serveur source et cible, consultez [création des fichiers de connexion de serveur &#40;AccessToSQL&#41; ](../../ssma/access/creating-the-server-connection-files-accesstosql.md) .  
  
-   **VariableValueFileSample.xml :** Toutes les variables qui ont été utilisés dans la console de l’exemple des fichiers de script et `ServersConnectionFileSample.xml` ont été assemblés dans ce fichier. Pour exécuter les exemples de scripts de console que l’utilisateur doit simplement remplacer la variable exemple valeurs avec l’utilisateur ceux définis et passer ce fichier comme un argument de ligne de commande supplémentaires, ainsi que le fichier de script.  
  
    Pour plus d’informations sur le fichier de valeurs variables, consultez [création de fichiers de valeur Variable &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md).  
  
-   **AssessmentReportGenerationSample.xml :** Cet exemple permet à l’utilisateur Générer un rapport d’évaluation xml qui peut être utilisé par l’utilisateur pour l’analyse avant de commencer à convertir et migrer des données.  
  
    Dans le `generate-assessment-report` l’utilisateur doit obligatoirement modifier la valeur de la variable de commande (reportez-vous **VariableValueFileSample.xml**) dans le `object-name` attribut le nom de base de données est en cours d’utilisation par l’utilisateur. Selon le type d’objet spécifié, le `object-type` valeur devra également être modifié.  
  
    Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `generate-assessment-report` 4 d’exemple de la commande de l’exemple de fichier de script de console.  
  
    Pour plus d’informations sur la génération de rapports, consultez [génération de rapports &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
    > [!NOTE]  
    > -   Assurez-vous que l’argument de ligne de commande de fichier de valeur de la variable est passée à l’application de console et VariableValueFileSample.xml est mis à jour avec l’utilisateur spécifié les valeurs.  
    > -   Assurez-vous qu’argument de ligne de commande de fichier de connexion serveur est passé à l’application de console et le ServersConnectionFileSample.xml est mis à jour avec les valeurs de paramètre de serveur correct.  
  
-   **ConversionAndDataMigrationSample.xml :** Cet exemple permet à l’utilisateur effectuer une migration de bout en bout à partir de la conversion de la migration des données. Vous trouverez ci-dessous la liste des valeurs d’attribut obligatoire qui devront modifier :  
  
    |Nom de la commande|Description|Attribute|  
    |----------------|---------------|-------------|  
    |`map-schema`|Mappage de schéma de base de données source vers le schéma cible.|`source-schema:` Spécifie la base de données source dont a besoin pour être converti.<br /><br />`sql-server-schema`: Spécifie la base de données cible qui doit être migré vers|  
    |`convert-schema`|Effectue une conversion de schéma à partir de la source vers le schéma cible.<br /><br />Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `convert-schema` 4 d’exemple de la commande de l’exemple de fichier de script de console.|`object-name`: Spécifiez la base de données source / nom qui nécessite d’être converti de l’objet. Vérifiez que le correspondant `object-type` est modifié en fonction du type d’objet qui est spécifié dans le `object-name`|  
    |`synchronize-target`|Synchronise les objets cibles avec la base de données cible.<br /><br />Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `synchronize-target` exemple 3 de la commande de l’exemple de fichier de script de console.|`object-name:` Spécifiez la base de données sql server / nom qui nécessite la création de l’objet. Vérifiez que le correspondant `object-type` est modifié en fonction du type d’objet qui est spécifié dans le `object-name`|  
    |`migrate-data`|Migre les données source vers la cible.<br /><br />Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `migrate-data` exemple 2 de la commande de l’exemple de fichier de script de console.|`object-name:` Spécifie la source de données / tables nom qui nécessite à migrer. Vérifiez que le correspondant `object-type` est modifié en fonction du type d’objet qui est spécifié dans le `object-name`|  
  
## <a name="see-also"></a>Voir aussi  
[Création de fichiers de la valeur de la Variable &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
[Création des fichiers de connexion de serveur &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
[Génération de rapports &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md)  
  
