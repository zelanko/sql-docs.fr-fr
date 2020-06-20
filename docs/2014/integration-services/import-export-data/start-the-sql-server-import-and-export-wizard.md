---
title: Exécuter l’Assistant importation et exportation SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 93ecd0b99ad355e38194afc338201790fba97684
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965579"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a>Exécuter l'Assistant Importation et Exportation SQL Server
  L'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] constitue la méthode la plus simple pour copier des données entre des sources de données et pour construire des packages de base. Pour plus d’informations sur l’Assistant, consultez [SQL Server Assistant importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
 Pour obtenir une vidéo qui montre comment utiliser l’Assistant importation et exportation SQL Server pour créer un package qui exporte des données à partir d’une base de données SQL Server vers une feuille de calcul Microsoft Excel, consultez [exportation de données SQL Server vers Excel (SQL Server vidéo)](https://go.microsoft.com/fwlink/?LinkId=131024).  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a>Pour démarrer l'Assistant Importation et Exportation SQL Server  
  
-   Dans le menu **Démarrer** , pointez sur **tous les programmes**, pointez sur**Microsoft SQL Server** , puis cliquez sur **Importer et exporter des données**.  
  
     -ou-  
  
     Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , cliquez avec le bouton droit sur le dossier **packages SSIS** , puis cliquez sur **Assistant SSISImport et exportation**.  
  
     -ou-  
  
     Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , dans le menu **projet** , cliquez sur **Assistant SSISImport et exportation**.  
  
     -ou-  
  
     Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)] type de serveur, développez bases de données, cliquez avec le bouton droit sur une base de données, pointez sur **tâches**, puis cliquez sur **importer des données** ou **exporter des données**.  
  
     -ou-  
  
     Dans une fenêtre d'invite de commandes, exécutez DTSWizard.exe qui se trouve dans C:\Program Files\Microsoft SQL Server\100\DTS\Binn.  
  
    > [!NOTE]  
    >  Sur un ordinateur 64 bits, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installe la version 64 bits de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DTSWizard.exe). Toutefois, certaines sources de données, telles qu'Access ou Excel, ne dispose que d'un fournisseur 32 bits. Pour utiliser ces sources de données, il peut s'avérer nécessaire d'installer et d'exécuter la version 32 bits de l'Assistant. Pour ce faire, sélectionnez Outils clients ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] lors de l'installation.  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a>Pour importer ou exporter des données à l'aide de l'Assistant Importation et Exportation SQL Server  
  
1.  Démarrez l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Sur les pages correspondantes de l'Assistant, sélectionnez une source de données et une destination de données.  
  
     Les sources de données disponibles comprennent des fournisseurs de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], des fournisseurs OLE DB, des fournisseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, des fournisseurs [!INCLUDE[vstecado](../../includes/vstecado-md.md)], Microsoft Office Excel, Microsoft Office Access et la source du fichier plat. En fonction de la source, vous définissez des options telles que le mode d'authentification, le nom du serveur, le nom de la base de données et le format de fichier.  
  
    > [!NOTE]  
    >  Le fournisseur de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider pour Oracle ne prend pas en charge les types de données Oracle BLOB, CLOB, NCLOB, BFILE et UROWID. Par conséquent, la source OLE DB ne peut pas extraire de données des tables qui contiennent des colonnes avec ces types de données.  
  
     Les destinations de données disponibles incluent les fournisseurs de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], les fournisseurs OLE DB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access et la destination de fichier plat.  
  
3.  Définissez les options pour le type de destination sélectionné.  
  
     Si la destination est une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier les éléments suivants :  
  
    -   Indiquez s'il faut créer une base de données et définir ses propriétés. Les propriétés suivantes ne peuvent pas être configurées et l'Assistant utilise les valeurs par défaut spécifiées :  
  
        |Propriété|Value|  
        |--------------|-----------|  
        |Classement|Latin1_General_CS_AS_KS_WS|  
        |mode de récupération|Full|  
        |Utiliser l'indexation de texte intégral|True|  
  
    -   Indiquez s'il faut copier des données à partir de tables ou de vues, ou copier des résultats de requête.  
  
         Si vous souhaitez interroger la source de données et copier les résultats, vous pouvez construire une requête Transact-SQL. Vous pouvez entrer la requête Transact-SQL manuellement ou utiliser une requête enregistrée dans un fichier. L'Assistant propose une fonctionnalité d'exploration qui vous permet de rechercher le fichier, et il l'ouvre et colle automatiquement son contenu dans la page de l'Assistant lorsque vous sélectionnez le fichier.  
  
         Si la source est un fournisseur [!INCLUDE[vstecado](../../includes/vstecado-md.md)], vous pouvez également utiliser l'option de copie des résultats de requête, en spécifiant la chaîne DBCommand en tant que requête.  
  
         Si la source de données est une vue, l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit automatiquement la vue en table dans la destination.  
  
    -   Indiquez si la table de destination est supprimée puis recréée, et si l'insertion d'identité doit être activée.  
  
    -   Indiquez s'il faut supprimer ou ajouter des lignes dans une table de destination existante. Si la table n'existe pas, l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la crée automatiquement.  
  
     Si la destination est un fichier plat, vous pouvez spécifier les éléments suivants :  
  
    -   Spécifier le séparateur de lignes dans le fichier de destination.  
  
    -   Spécifier le délimiteur de colonne dans le fichier de destination.  
  
4.  (Facultatif) Sélectionnez une table et modifiez les mappages entre les colonnes sources et de destination, ou modifiez les métadonnées des colonnes de destination :  
  
    -   Mappez les colonnes sources à des colonnes de destination différentes.  
  
    -   Modifiez le type de données dans la colonne de destination.  
  
    -   Définissez la longueur des colonnes avec des types de données character.  
  
    -   Définissez la précision et l'échelle des colonnes avec des types de données numériques.  
  
    -   Indiquez si la colonne peut contenir des valeurs Null.  
  
5.  (Facultatif) Sélectionnez plusieurs tables, et mettez à jour les métadonnées et options à appliquer à ces tables :  
  
    -   Sélectionnez un schéma de destination existant ou fournissez un nouveau schéma auquel affecter les tables.  
  
    -   Indiquez si les insertions d'identité doivent être activées dans les tables de destination.  
  
    -   Indiquez si les tables de destination doivent être supprimées et recréées.  
  
    -   Indiquez si les tables de destination existantes doivent être tronquées.  
  
6.  Enregistrez et exécutez un package.  
  
     Si l'Assistant est démarré à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de l'invite de commandes, le package peut s'exécuter immédiatement. Vous pouvez éventuellement enregistrer le package dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données **msdb** ou dans le système de fichiers. Pour plus d’informations sur la base de données **msdb** , consultez [Package Management &#40;service SSIS&#41;](../service/package-management-ssis-service.md).  
  
     Lorsque vous enregistrez le package, vous pouvez définir son niveau de protection et, si ce niveau utilise un mot de passe, fournir celui-ci. Pour plus d’informations sur les niveaux de protection des packages, consultez [Access Control pour obtenir des données sensibles dans des packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Si l'Assistant est démarré à partir d'un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous ne pouvez pas exécuter le package à partir de l'Assistant. Au lieu de cela, le package est ajouté au projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à partir duquel vous avez démarré l'Assistant. Vous pouvez ensuite exécuter le package dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], l'option permettant d'enregistrer le package créé par l'Assistant n'est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant importation et exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Créer des packages dans les outils de données SQL Server](../create-packages-in-sql-server-data-tools.md)  
  
  
