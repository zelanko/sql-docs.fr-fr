---
title: Le chargement converti objets base de données dans SQL Server (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, loading converted objects into SQL Azure
- Access databases, loading converted objects into SQL Server
- data, securing
- loading objects into SQL Azure
- loading objects into SQL Server
- migrating objects into SQL Azure
- migrating objects into SQL Server
- moving objects into SQL Azure
- moving objects into SQL Server
- schemas, loading into SQL Azure
- schemas, loading into SQL Server
- scripting converted objects
- securing data
- SQL Azure, loading objects into
- SQL Server, loading objects into
- synchronizing metadata with SQL Azure
- synchronizing metadata with SQL Server
- uploading objects into SQL Azure
- uploading objects into SQL Server
ms.assetid: 4e854eee-b10c-4f0b-9d9e-d92416e6f2ba
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9ab56815fa36f23a15bc646c69094c3ca2f5fa3e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299247"
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Le chargement converti objets base de données dans SQL Server (AccessToSQL)
Après avoir converti les objets de base de données Access à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous pouvez charger les objets de base de données qui en résulte dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous pouvez avoir créer les objets SSMA, ou vous pouvez générer un script les objets et exécuter les scripts vous-même. En outre, SSMA vous permet de mettre à jour des métadonnées de la cible avec le contenu réel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Choix entre synchronisation et de Scripts  
Si vous souhaitez charger les objets de base de données convertie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure sans modification, vous pouvez avoir SSMA directement de créer ou de recréer les objets de base de données. Cette méthode est simple et rapide, mais ne permettent pas de personnaliser la [!INCLUDE[tsql](../../includes/tsql-md.md)] code qui définit le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des objets de SQL Azure, autres que les procédures stockées.  
  
Si vous souhaitez modifier le [!INCLUDE[tsql](../../includes/tsql-md.md)] qui est utilisé pour créer des objets, ou si vous souhaitez davantage de contrôle sur la création d’objets, utilisez SSMA pour créer des scripts. Vous pouvez ensuite modifier ces scripts, créer chaque objet individuellement et même utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour planifier la création de ces objets.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>À l’aide de SSMA pour synchroniser des objets avec SQL Server  
Utilisation de SSMA pour créer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de base de données SQL Azure, vous sélectionnez les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure et synchronisez ensuite les objets avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, comme indiqué dans la procédure suivante. Par défaut, si les objets existent déjà dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure et si les métadonnées SSMA ont certaines modifications locales ou les mises à jour de la définition de ces objets très, SSMA modifiera les définitions d’objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous pouvez modifier le comportement par défaut en modifiant **paramètres du projet**.  
  
> [!NOTE]  
> Vous pouvez sélectionner existant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des objets de base de données SQL Azure qui n’ont pas été converties à partir de bases de données Access. Toutefois, SSMA ne sera pas recréer ou de modifier ces objets.  
  
**Pour synchroniser des objets avec SQL Server ou SQL Azure**  
  
1.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l’Explorateur de métadonnées SQL Azure, développez haut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou nœud de SQL Azure, puis développez **bases de données**.  
  
2.  Sélectionnez les objets à traiter :  
  
    -   Pour synchroniser une base de données complète, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour synchroniser ou omettre des objets individuels ou des catégories d’objets, activez ou désactivez la case à cocher en regard de l’objet ou un dossier.  
  
3.  Une fois que vous avez sélectionné les objets à traiter dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l’Explorateur de métadonnées SQL Azure, avec le bouton droit **bases de données**, puis cliquez sur **synchroniser avec la base de données**.  
  
    Vous pouvez également synchroniser des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **synchroniser avec la base de données**.  
  
    Après cela, SSMA affichera le **synchroniser avec la base de données** boîte de dialogue, où vous pouvez voir les deux groupes d’éléments. Sur le côté gauche, SSMA affiche les objets de base de données sélectionnée représentées dans une arborescence. Sur le côté droit, vous pouvez voir une arborescence représentant les mêmes objets dans les métadonnées SSMA. Vous pouvez développer l’arborescence en cliquant sur la droite ou gauche bouton « + ». La direction de la synchronisation est indiquée dans la colonne d’Action placée entre les deux arborescences.  
  
    Un signe de l’action peut être dans trois états :  
  
    -   Une flèche gauche signifie que le contenu de métadonnées est enregistré dans la base de données (la valeur par défaut).  
  
    -   Une flèche droite signifie le contenu de la base de données remplacent les métadonnées SSMA.  
  
    -   Une croix signifie qu'aucune action n’est entreprise.  
  
    Cliquez sur le signe de l’action pour modifier l’état. Véritable synchronisation sera effectuée lorsque vous cliquez sur **OK** bouton de la **synchroniser avec la base de données** boîte de dialogue.  
  
## <a name="scripting-objects"></a>Objets de script  
Si vous souhaitez enregistrer [!INCLUDE[tsql](../../includes/tsql-md.md)] définitions des objets de base de données convertie, ou vous souhaitez modifier les définitions d’objets et exécuter des scripts vous-même, vous pouvez enregistrer des définitions d’objet dans la base de données convertie [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.  
  
**Pour enregistrer un ou plusieurs objets dans un script**  
  
1.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, développez le nœud supérieur (le nom du serveur), puis **bases de données**.  
  
2.  Effectuez une ou plusieurs des opérations suivantes :  
  
    -   Pour générer un script une base de données complète, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour générer un script ou omettre les vues individuelles, développez la base de données, puis **vues**, puis sélectionnez ou désactivez la case à cocher en regard de la vue.  
  
    -   Pour générer un script ou omettre des tables individuelles, développez la base de données, puis **Tables**, puis sélectionnez ou désactivez la case à cocher en regard du tableau.  
  
    -   Pour générer un script ou omettre des index individuels pour une table, développez la table, **index**et puis activez ou désactivez l’index.  
  
3.  Avec le bouton droit **bases de données** et sélectionnez **enregistrer en tant que Script**.  
  
    Vous pouvez également créer un script des objets individuels. Pour générer un script un objet, quelles que soient les objets sont sélectionnés, cliquez sur l’objet et sélectionnez **enregistrer en tant que Script**.  
  
4.  Dans le **enregistrer en tant que** boîte de dialogue, recherchez le dossier où vous souhaitez enregistrer le script, entrez un nom de fichier dans le **nom de fichier** , puis cliquez sur **OK**.  
  
    SSMA permet d’ajouter l’extension de nom de fichier .sql.  
  
### <a name="modifying-scripts"></a>Modification des Scripts  
Une fois que vous avez enregistré le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou définitions d’objets SQL Azure en tant que script, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour modifier le script.  
  
**Pour modifier un script**  
  
1.  Sur le [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Dans le **Open** boîte de dialogue, recherchez et sélectionnez votre fichier de script, puis cliquez sur **OK**.  
  
3.  Modifiez le fichier de script à l’aide de l’éditeur de requête.  
  
    Pour plus d’informations sur l’éditeur de requête, consultez « Éditeur de commandes et fonctionnalités pratiques » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
4.  Pour enregistrer le script, dans le menu fichier, sélectionnez **enregistrer**.  
  
### <a name="running-scripts"></a>Exécution de Scripts  
Vous pouvez exécuter un script ou des instructions individuelles, en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Pour exécuter un script**  
  
1.  Sur le [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **fichier** menu, pointez sur **Open** puis cliquez sur **fichier**.  
  
2.  Dans le **Open** boîte de dialogue, recherchez et sélectionnez votre fichier de script, puis cliquez sur **OK**.  
  
3.  Pour exécuter le script complet, appuyez sur la **F5** clé.  
  
4.  Pour exécuter un ensemble d’instructions, les instructions select dans la fenêtre d’éditeur de requête, puis appuyez sur la **F5** clé.  
  
Pour plus d’informations sur l’utilisation de l’éditeur de requête pour exécuter des scripts, consultez « [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] requête » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
Vous pouvez également exécuter des scripts à partir de la ligne de commande à l’aide de la **sqlcmd** utilitaire et à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Pour plus d’informations sur **sqlcmd**, consultez « utilitaire sqlcmd » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, voir « Automatisation des tâches d’administration ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent) » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="securing-objects-in-sql-server"></a>Sécurisation des objets dans SQL Server  
Une fois que vous avez chargé les objets de base de données convertie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez accorder et refuser des autorisations sur ces objets. Il est judicieux de le faire avant de migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la sécurisation des objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez « Sécurité considérations relatives à des bases de données et base de données des Applications » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration est [migrer des données dans SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
