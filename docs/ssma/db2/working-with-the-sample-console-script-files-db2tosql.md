---
title: Utilisation des fichiers de Script de Console exemple (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5c3080c3-d074-4f99-a5f5-219ebeddc474
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e109713ce9f6ec29a31d19d873c319d47c76fdab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675497"
---
# <a name="working-with-the-sample-console-script-files-db2tosql"></a>Utilisation des fichiers de Script de Console exemple (DB2ToSQL)
Quelques exemples de fichiers ont été fournis, ainsi que le produit pour la référence de l’utilisateur et l’utilisation. Cette section décrit la façon de personnaliser facilement ces scripts en fonction des besoins des utilisateurs finaux.  
  
## <a name="sample-console-script-files"></a>Exemples de fichiers de Script Console  
Les fichiers de script de console exemple suivants couvrant différents scénarios ont été fournies pour la référence de l’utilisateur :  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
1.  **ServersConnectionFileSample.xml :**  
  
    -   Cet exemple donne les différents modes de connexion disponible à la base de données source et cible et l’utilisateur peut sélectionner n’importe quel mode selon les besoins. Cet exemple contient les définitions de serveur.  
  
    -   L’utilisateur peut se connecter à la base de données requis en modifiant simplement les valeurs à la source requis et les définitions de serveur cible. Dans l’exemple fourni toutes les valeurs ont été fournies comme variable les valeurs qui sont disponibles dans le **VariableValueFileSample.xml**.  Tous les autres paramètres de connexion peuvent être supprimés du fichier de connexion de serveur de travail de l’utilisateur.  
  
    -   Pour plus d’informations sur la connexion au serveur source et cible, consultez [création des fichiers de connexion de serveur &#40;DB2ToSQL&#41; ](../../ssma/db2/creating-the-server-connection-files-db2tosql.md) .  
  
2.  **VariableValueFileSample.xml :** toutes les variables qui ont été utilisés dans la console de l’exemple des fichiers de script et `ServersConnectionFileSample.xml` ont été assemblés dans ce fichier. Pour exécuter les exemples de scripts de console que l’utilisateur doit simplement remplacer la variable exemple valeurs avec l’utilisateur ceux définis et passer ce fichier comme un argument de ligne de commande supplémentaires, ainsi que le fichier de script.  
  
    Pour plus d’informations sur le fichier de valeurs variables, consultez [création de fichiers de valeur Variable &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md).  
  
3.  **AssessmentReportGenerationSample.xml :** cet exemple permet à l’utilisateur Générer un rapport d’évaluation xml qui peut être utilisé par l’utilisateur pour l’analyse avant de commencer à convertir et migrer des données.  
  
    Dans le `generate-assessment-report` l’utilisateur doit obligatoirement modifier la valeur de la variable de commande (reportez-vous **VariableValueFileSample.xml**) dans le `object-name` attribut le nom de base de données est en cours d’utilisation par l’utilisateur. Selon le type d’objet spécifié, le `object-type` valeur devra également être modifié.  
  
    Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `generate-assessment-report` 4 d’exemple de la commande de l’exemple de fichier de script de console.  
  
    Pour plus d’informations sur la génération de rapports, consultez [génération de rapports &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
    **Remarques :**  
  
    Assurez-vous que l’argument de ligne de commande de fichier de valeur de la variable est passée à l’application de console et VariableValueFileSample.xml est mis à jour avec l’utilisateur spécifié les valeurs.  
  
    Assurez-vous qu’argument de ligne de commande de fichier de connexion serveur est passé à l’application de console et le ServersConnectionFileSample.xml est mis à jour avec les valeurs de paramètre de serveur correct.  
  
4.  **SqlStatementConversionSample.xml :** cet exemple permet à l’utilisateur Générer le correspondantes `t-sql` script pour la base de données source `sql` commande fournie en tant qu’entrée.  
  
    Dans le `convert-sql-statement` l’utilisateur doit obligatoirement modifier la valeur de la variable de commande (reportez-vous **VariableValueFileSample.xml**) dans le `context` nom à l’attribut de base de données qui est en cours d’utilisation par l’utilisateur. L’utilisateur sera également être requises pour modifier le `sql` valeur d’attribut à la base de données source `sql` commande nécessitant une qu’il doit être convertie.  
  
    L’utilisateur peut également fournir des fichiers sql à convertir. Cela a été illustré dans la `convert-sql-statement` 4 d’exemple de la commande de l’exemple de fichier de script de console.  
  
    > [!NOTE]  
    > Assurez-vous que l’argument de ligne de commande de fichier de valeur de la variable est passée à l’application de console et VariableValueFileSample.xml est mis à jour avec l’utilisateur spécifié les valeurs.  
  
5.  **ConversionAndDataMigrationSample.xml :** cet exemple permet à l’utilisateur effectuer une migration de bout en bout à partir de la conversion de la migration des données. Vous trouverez ci-dessous la liste des valeurs d’attribut obligatoire qui devront modifier :  
  
    |Nom de la commande|Description|Attribute|  
    |----------------|---------------|-------------|  
    |`map-schema`|Mappage de schéma de base de données source vers le schéma cible.|`source-schema:` Spécifie la base de données source dont a besoin pour être converti.<br /><br />`sql-server-schema`: Spécifie la base de données cible qui doit être migré vers|  
    |`convert-schema`|Effectue une conversion de schéma à partir de la source vers le schéma cible.<br /><br />Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `convert-schema` 4 d’exemple de la commande de l’exemple de fichier de script de console.|`object-name`: Permet de spécifier la base de données source / nom qui nécessite d’être converti de l’objet. Vérifiez que le correspondant `object-type` est modifié en fonction du type d’objet qui est spécifié dans le `object-name`|  
    |`synchronize-target`|Synchronise les objets cibles avec la base de données cible.<br /><br />Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `synchronize-target` exemple 3 de la commande de l’exemple de fichier de script de console.|`object-name:` Spécifiez la base de données sql server / nom qui nécessite la création de l’objet. Vérifiez que le correspondant `object-type` est modifié en fonction du type d’objet qui est spécifié dans le `object-name`|  
    |`migrate-data`|Migre les données source vers la cible.<br /><br />Si l’utilisateur a évaluer plusieurs objets ou des bases de données qu’il peut spécifier plusieurs `metabase-object` nœuds, comme illustré dans le `migrate-data` exemple 2 de la commande de l’exemple de fichier de script de console.|`object-name:` Spécifie la source de données / tables nom qui nécessite à migrer. Vérifiez que le correspondant `object-type` est modifié en fonction du type d’objet qui est spécifié dans le `object-name`|  
  
## <a name="see-also"></a>Voir aussi  
[Création de fichiers de la valeur de la Variable &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
[Création des fichiers de connexion de serveur &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
[Génération de rapports &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)  
  
