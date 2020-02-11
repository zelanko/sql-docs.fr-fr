---
title: Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 790e509dd29e388dfb697ba577958395a4a046ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66072885"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite
  Il existe souvent des situations où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] souhaite modifier le mode lecture/écriture d'une base de données tabulaire ou multidimensionnelle. Ces situations sont souvent justifiées par des exigences opérationnelles, telles que le partage de la base de données au sein d'un pool de serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour un plus grand confort de l'utilisateur.  
  
 Vous pouvez basculer d'un mode de base de données à un autre de différentes façons. Ce document explique les scénarios courants suivants :  
  
-   Par interaction à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   Par programmation à l'aide d'AMO  
  
-   Par script à l'aide de XMLA  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Pour basculer interactivement le mode lecture/écriture d'une base de données à l'aide de Management Studio  
  
1.  Localisez la base de données à basculer dans le volet gauche ou droit de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Cliquez avec le bouton droit sur la base de données et sélectionnez **Propriétés**. Recherchez le dossier de base de données et notez l'emplacement. Un emplacement de stockage de base de données vide indique que le dossier de base de données se trouve dans le dossier de données de serveur.  
  
    > [!IMPORTANT]  
    >  Dès que la base de données est détachée, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ne peut plus vous aider à obtenir l'emplacement de base de données.  
  
3.  Cliquez avec le bouton droit sur la base de données et sélectionnez **détacher...**  
  
4.  Assignez un mot de passe à la base de données à détacher, puis cliquez sur **OK** pour exécuter la commande de détachement.  
  
5.  Localisez le dossier **bases de données** dans le volet gauche ou [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]droit de.  
  
6.  Cliquez avec le bouton droit sur le dossier **bases de données** , puis sélectionnez **attacher...**  
  
7.  Dans la zone de texte **dossier** , tapez l'emplacement d'origine du dossier de base de données. Vous pouvez également utiliser le bouton Parcourir (**...**) pour rechercher le dossier de base de données.  
  
8.  Sélectionnez le mode lecture/écriture pour la base de données.  
  
9. Tapez le mot de passe utilisé à l’étape 3, puis cliquez sur **OK** pour exécuter la commande d’attachement.  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>Pour basculer par programmation le mode lecture/écriture sur une base de données à l'aide d'AMO  
  
1.  Dans votre application C#, adaptez l'exemple de code suivant et complétez les tâches indiquées.  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  Dans votre application C#, appelez `SwitchReadWrite()` avec les paramètres nécessaires.  
  
2.  Compilez et exécutez le code pour déplacer la base de données.  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>Pour basculer le mode lecture/écriture sur une base de données par script à l'aide de XMLA  
  
1.  Localisez la base de données à basculer dans le volet gauche ou droit de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Cliquez avec le bouton droit sur la base de données et sélectionnez **Propriétés**. Recherchez le dossier de base de données et notez l'emplacement. Un emplacement de stockage de base de données vide indique que le dossier de base de données se trouve dans le dossier de données de serveur.  
  
    > [!IMPORTANT]  
    >  Dès que la base de données est détachée, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ne peut plus vous aider à obtenir l'emplacement de base de données.  
  
3.  Ouvrez un nouvel onglet XMLA dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
4.  Copiez le modèle de script suivant pour XMLA :  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  Remplacez `%dbName%` par le nom de la base de données et `%password%` par le mot de passe. Les caractères % font partie du modèle et doivent être supprimés.  
  
2.  Exécutez la commande XMLA.  
  
3.  Copiez le modèle de script suivant pour XMLA dans un nouvel onglet XMLA.  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  Remplacez `%dbFolder%` par le chemin UNC complet du dossier de base de données, `%ReadOnlyMode%` par la valeur `ReadOnly` correspondante ou `ReadWrite`, et `%password%` par le mot de passe. Les caractères % font partie du modèle et doivent être supprimés.  
  
2.  Exécutez la commande XMLA.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Emplacement de stockage de base de données](database-storage-location.md)   
 [ReadWriteModes de base de données](database-readwritemodes.md)   
 [Élément Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Détacher l’élément](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Élément ReadWriteMode](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element)   
 [Élément DbStorageLocation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
