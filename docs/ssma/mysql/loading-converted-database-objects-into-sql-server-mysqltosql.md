---
title: Le chargement converti objets base de données dans SQL Server (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b2e58eb534088482493e6f36c3841f36644183af
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63187231"
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>Chargement d’objets de base de données convertis dans SQL Server (MySQLToSQL)
Après avoir converti les bases de données MySQL vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous pouvez charger les objets de base de données qui en résulte dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous pouvez avoir créer les objets SSMA, ou vous pouvez générer un script les objets et exécuter les scripts vous-même. En outre, SSMA vous permet de mettre à jour des métadonnées de la cible avec le contenu réel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Choix entre synchronisation et de Scripts  
Si vous souhaitez charger les objets de base de données convertie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure sans modification, vous pouvez avoir SSMA directement de créer ou de recréer les objets de base de données. Que la méthode est simple et rapide, mais ne permettent pas de personnaliser le code Transact-SQL qui définit le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de SQL Azure.  
  
Si vous souhaitez modifier le Transact-SQL qui est utilisé pour créer des objets, ou si vous souhaitez contrôler davantage la création d’objets, utilisez SSMA pour créer des scripts. Vous pouvez ensuite modifier ces scripts, créez chaque objet individuellement et même utiliser SQL Server Agent pour planifier la création de ces objets.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>À l’aide de SSMA pour synchroniser des objets avec SQL Server  
Pour utiliser SSMA pour créer des objets de base de données SQL Server ou SQL Azure, vous sélectionnez les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure, puis synchronisez les objets avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, comme indiqué dans la procédure suivante. Par défaut, si les objets existent déjà dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure et si les métadonnées SSMA ont certaines modifications locales ou les mises à jour de la définition de ces objets très, SSMA modifiera les définitions d’objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous pouvez modifier le comportement par défaut en modifiant **paramètres du projet**.  
  
> [!NOTE]  
> Vous pouvez sélectionner existant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des objets de base de données SQL Azure qui n’ont pas été converties à partir de bases de données MySQL. Toutefois, ces objets ne seront pas recréés ou modifiés par SSMA.  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>Pour synchroniser des objets avec SQL Server ou SQL Azure  
  
1.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l’Explorateur de métadonnées SQL Azure, développez haut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou nœud de SQL Azure, puis développez **bases de données**.  
  
2.  Sélectionnez les objets à traiter :  
  
    -   Pour synchroniser une base de données complète, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour synchroniser ou omettre des objets individuels ou des catégories d’objets, activez ou désactivez la case à cocher en regard de l’objet ou un dossier.  
  
3.  Une fois que vous avez sélectionné les objets à traiter dans SQL Server ou l’Explorateur de métadonnées SQL Azure, cliquez sur **bases de données**, puis cliquez sur **synchroniser avec la base de données**.  
  
    Vous pouvez également synchroniser des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **synchroniser avec la base de données**.  
  
    Après cela, SSMA affichera le **synchroniser avec la base de données** boîte de dialogue, où vous pouvez voir les deux groupes d’éléments. Sur le côté gauche, SSMA affiche les objets de base de données sélectionnée représentées dans une arborescence. Sur le côté droit, vous pouvez voir une arborescence représentant les mêmes objets dans les métadonnées SSMA. Vous pouvez développer l’arborescence en cliquant sur la droite ou gauche bouton « + ». La direction de la synchronisation est indiquée dans la colonne d’Action placée entre les deux arborescences.  
  
    Un signe de l’action peut être dans trois états suivants :  
  
    -   Une flèche gauche signifie que le contenu de métadonnées est enregistré dans la base de données (la valeur par défaut).  
  
    -   Une flèche droite signifie le contenu de la base de données remplacent les métadonnées SSMA.  
  
    -   Une croix signifie qu'aucune action n’est entreprise.  
  
    -   Cliquez sur le signe de l’action pour modifier l’état. Véritable synchronisation sera effectuée lorsque vous cliquez sur **OK** bouton de la **synchroniser avec la base de données** boîte de dialogue.  
  
## <a name="scripting-objects"></a>Objets de script  
Pour enregistrer [!INCLUDE[tsql](../../includes/tsql-md.md)] définitions des objets de base de données convertie, ou modifier les définitions d’objet et d’exécuter des scripts vous-même, vous pouvez enregistrer la base de données convertie définitions d’objet dans [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.  
  
**Pour enregistrer les objets en tant que scripts**  
  
1.  Avec le bouton droit une fois que vous avez sélectionné les objets à enregistrer dans un script, **bases de données**, puis cliquez sur **enregistrer en tant que Script**.  
  
    Vous pouvez également créer un script des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **enregistrer en tant que Script**.  
  
2.  Dans le **enregistrer en tant que** boîte de dialogue, recherchez le dossier où vous souhaitez enregistrer le script, entrez un nom de fichier dans le **nom de fichier** boîte, puis [!INCLUDE[clickOK](../../includes/clickok-md.md)] SSMA permet d’ajouter l’extension de nom de fichier .sql.  
  
### <a name="modifying-scripts"></a>Modification des Scripts  
Une fois que vous avez enregistré le SQL Server ou les définitions d’objets SQL Azure dans un script, vous pouvez utiliser SQL Server Management Studio pour modifier le script.  
  
**Pour modifier un script**  
  
1.  Dans Management Studio **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Dans la boîte de dialogue Ouvrir, recherchez et sélectionnez votre fichier de script, puis cliquez sur **OK**.  
  
3.  Modifiez le fichier de script à l’aide de l’éditeur de requête. Pour plus d’informations sur l’éditeur de requête, consultez « Éditeur de commandes et fonctionnalités pratiques » dans la documentation en ligne de SQL Server.  
  
4.  Pour enregistrer le script, dans le menu fichier, sélectionnez **enregistrer**.  
  
### <a name="running-scripts"></a>Exécution de Scripts  
Vous pouvez exécuter un script ou des instructions individuelles, dans SQL Server Management Studio.  
  
**Pour exécuter un script**  
  
1.  Sur le serveur SQL Server Management Studio **fichier** menu, pointez sur **Open** puis cliquez sur **fichier**.  
  
2.  Dans la boîte de dialogue Ouvrir, recherchez et sélectionnez votre fichier de script, puis cliquez sur **OK**.  
  
3.  Pour exécuter le script complet, appuyez sur la **F5** clé.  
  
4.  Pour exécuter un ensemble d’instructions, les instructions select dans la fenêtre d’éditeur de requête, puis appuyez sur la **F5** clé.  
  
5.  Pour plus d’informations sur l’utilisation de l’éditeur de requête pour exécuter des scripts, consultez « SQL Server Management Studio requête Transact-SQL » dans la documentation en ligne de SQL Server.  
  
6.  Vous pouvez également exécuter des scripts à partir de la ligne de commande à l’aide de la **sqlcmd** utilitaire et à partir de l’Agent SQL Server. Pour plus d’informations sur **sqlcmd**, consultez « utilitaire sqlcmd » dans la documentation en ligne de SQL Server. Pour plus d’informations sur l’Agent SQL Server, consultez « Automating tâches administratives (Agent SQL Server) » dans la documentation en ligne de SQL Server.  
  
## <a name="securing-objects-in-sql-server"></a>Sécurisation des objets dans SQL Server  
Une fois que vous avez chargé les objets de base de données convertis dans SQL Server, vous pouvez accorder et refuser des autorisations sur ces objets. Il est judicieux de le faire avant de migrer des données dans SQL Server. Pour plus d’informations sur la façon de sécuriser les objets dans SQL Server, consultez « Sécurité considérations relatives à des bases de données et base de données des Applications » dans la documentation en ligne de SQL Server.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration est [migration des données de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
