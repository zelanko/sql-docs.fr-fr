---
title: "Convertir des objets de base de données ASE Sybase (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c26c897ef9b4ffe1a05a47ab722770681a3737a8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="converting-sybase-ase-database-objects-sybasetosql"></a>Convertir des objets de base de données ASE Sybase (SybaseToSQL)
Après vous être connecté pour Sybase Adaptive Server Enterprise (ASE), connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure et définir le projet et les options de mappage de données, vous pouvez convertir des objets de base de données Sybase Adaptive Server Enterprise (ASE) à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou des objets de base de données SQL Azure.  
  
## <a name="the-conversion-process"></a>Le processus de Conversion  
Convertir des objets de base de données accepte les définitions d’objets à partir de ASE, les convertit en similaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure objets et charge ensuite ces informations dans les métadonnées SSMA. Il ne charge pas les informations dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure. Vous pouvez ensuite afficher les objets et leurs propriétés à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou de l’Explorateur de métadonnées SQL Azure.  
  
Lors de la conversion, SSMA imprime la sortie des messages vers le volet de sortie et messages d’erreur dans le volet de la liste d’erreurs. Utilisez les informations de sortie et d’erreur pour déterminer si vous devez modifier vos bases de données ASE ou votre processus de conversion pour obtenir les résultats de la conversion souhaitée.  
  
## <a name="setting-conversion-options"></a>Définition des Options de Conversion  
Avant de convertir les objets, vérifiez les options de conversion de projet dans le **les paramètres de projet** boîte de dialogue. À l’aide de cette boîte de dialogue, vous pouvez définir comment SSMA convertit les fonctions et variables globales. Pour plus d’informations, consultez [paramètres du projet &#40; Conversion de &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>Convertir des objets de base de données ASE  
Pour convertir des objets de base de données ASE, vous tout d’abord sélectionnez les objets que vous souhaitez convertir et puis SSMA effectuer la conversion. Pour afficher les messages de sortie lors de la conversion, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour convertir des objets de ASE à la syntaxe SQL Server ou SQL Azure**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, développez le serveur ASE, puis **bases de données**.  
  
2.  Sélectionner les objets à convertir :  
  
    -   Pour convertir toutes les bases de données, sélectionnez la case à cocher à côté **bases de données**.  
  
    -   Pour convertir ou omettre une base de données, activez ou désactivez la case à cocher en regard du nom de la base de données.  
  
    -   Pour convertir ou omettre des schémas individuels, développez la base de données, **schémas**, puis activez ou désactivez la case à cocher en regard du schéma.  
  
    -   Pour convertir ou omettre une catégorie d’objets, développez le schéma, puis sélectionnez ou désactivez la case à cocher en regard de la catégorie.  
  
    -   Pour convertir ou omettre des objets, développez le dossier de la catégorie, puis sélectionnez ou désactivez la case à cocher en regard de l’objet.  
  
3.  Pour convertir tous les objets sélectionnés, cliquez sur **bases de données** et sélectionnez **convertir un schéma**.  
  
    Vous pouvez également convertir des objets individuels ou des catégories d’objets en cliquant sur l’objet ou son conteneur, puis en sélectionnant **convertir un schéma**.  
  
> [!NOTE]  
> Certaines fonctions système Sybase ne correspondent pas exactement les fonctions de système de SQL Server équivalentes de comportement. Pour émuler le comportement de Sybase ASE, SSMA génère des fonctions définies par l’utilisateur dans la base de données SQL Server converti sous un schéma nommé 's2ss'. Selon les paramètres de projet, certaines fonctions système SQL Server sont remplacés avec ces fonctions émulées. SSMA crée les fonctions définies par l’utilisateur suivantes :  
  
||||  
|-|-|-|  
|**char_length_nvarchar**|**index_colorder**|**ssma_datepart**|  
|**char_length_varchar**|**donnéesINTTOHEX**|**substring_nvarchar**|  
|**charindex_nvarchar**|**ssma_datediff**|**substring_varbinary**|  
|**charindex_varchar**|**HEXTOINT**|**substring_varchar**|  
|**ulowsurr**|**to_unichar**|**ssma_current_time**|  
|**uhighsurr**|||  
  
## <a name="objects-not-supported-in-sql-azure"></a>Objets non pris en charge dans SQL Azure  
Les mots clés de T-SQL suivants sont utilisés par SSMA pour Sybase pendant la conversion standard de SQL Server, mais ces mots clés ne sont pas pris en charge par la syntaxe T-SQL de SQL Azure :  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE/ALTER/DROP DEFAULT|CREATE/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|GRANT/REVOKE/DENY DE ALL|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## <a name="viewing-conversion-problems"></a>Affichage des problèmes de Conversion  
Certains objets ASE ne peuvent pas convertir. Vous pouvez déterminer le taux de réussite de conversion en affichant le rapport de synthèse de conversion.  
  
**Pour afficher un rapport de synthèse**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez **bases de données**.  
  
2.  Dans le volet droit, sélectionnez le **rapport** onglet.  
  
    Ce rapport affiche le rapport d’évaluation de synthèse pour tous les objets de base de données qui ont été évaluée ou converti. Vous pouvez également afficher un rapport de synthèse pour des objets :  
  
    -   Pour afficher le rapport pour une base de données individuel, sélectionnez la base de données dans l’Explorateur de métadonnées de Sybase.  
  
    -   Pour afficher le rapport pour un objet de base de données individuels, sélectionnez l’objet dans l’Explorateur de métadonnées Sybase. Les objets qui ont des problèmes de conversion ont une icône d’erreur rouge.  
  
Pour les objets en échec de conversion, vous pouvez afficher la syntaxe qui a entraîné l’échec de la conversion.  
  
**Pour afficher les problèmes de conversion individuels**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, développez **bases de données**.  
  
2.  Développez la base de données qui affiche une icône d’erreur rouge.  
  
3.  Développez le **schémas** dossier, puis développez le schéma qui affiche une icône d’erreur rouge.  
  
4.  Sous le schéma, développez un dossier qui a une icône d’erreur rouge.  
  
5.  Sélectionnez l’objet qui a une icône d’erreur rouge.  
  
6.  Dans le volet droit, cliquez sur le **rapport** onglet.  
  
7.  En haut de la **rapport** onglet est une liste déroulante. Si la liste affiche **statistiques**, modifiez la sélection à **Source**.  
  
    SSMA affichera le code source et plusieurs boutons immédiatement au-dessus du code.  
  
8.  Cliquez sur le **problème suivant** bouton. Il s’agit d’une icône d’erreur rouge avec une flèche pointant vers la droite.  
  
    SSMA pour ASE met en surbrillance le premier code source problématiques qu’elle trouve dans l’objet actuel.  
  
Pour chaque élément ne peut pas être converti, vous devez déterminer ce que vous voulez faire avec cet objet :  
  
-   Vous pouvez modifier le code source des procédures et des déclencheurs sur les **SQL** onglet.  
  
-   Vous pouvez modifier l’objet ASE pour supprimer ou modifier tout code problématique. Pour charger le code mis à jour dans SSMA, vous devez mettre à jour les métadonnées. Pour plus d’informations, consultez [la connexion à Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou l’Explorateur de métadonnées SQL Azure et l’Explorateur de métadonnées Sybase, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure et la migration des données à partir de ASE.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [le chargement des objets de base de données convertie dans SQL Server / SQL Azure (SybaseToSQL)](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06).  
  
## <a name="see-also"></a>Voir aussi  
[Migration Sybase ASE bases de données SQL Server : base de données SQL Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
