---
title: Le chargement converti objets base de données dans SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Synchronization, Securing Objects in SQL Server
- Synchronization,Scripting Objects
ms.assetid: a8ae33b2-1883-4785-922b-ea0e31c0b37a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 31b7f6b63aadd36d9d933da27a817adea9aeb9ac
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982271"
---
# <a name="loading-converted-database-objects-into-sql-server-oracletosql"></a>Le chargement converti objets base de données dans SQL Server (OracleToSQL)
Après avoir converti les schémas Oracle vers SQL Server, vous pouvez charger les objets de base de données qui en résulte dans SQL Server. Vous pouvez avoir créer les objets SSMA, ou vous pouvez générer un script les objets et exécuter les scripts vous-même. En outre, SSMA vous permet de mettre à jour des métadonnées de la cible avec le contenu réel de la base de données SQL Server.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Choix entre synchronisation et de Scripts  
Si vous souhaitez charger les objets de base de données convertis dans SQL Server sans modification, vous pouvez avoir SSMA directement de créer ou de recréer les objets de base de données. Que la méthode est simple et rapide, mais ne permettent pas de personnaliser le [!INCLUDE[tsql](../../includes/tsql_md.md)] code qui définit les objets SQL Server, autres que des procédures stockées.  
  
Si vous souhaitez modifier le [!INCLUDE[tsql](../../includes/tsql_md.md)] qui est utilisé pour créer des objets, ou si vous souhaitez davantage de contrôle sur la création d’objets, utilisez SSMA pour créer des scripts. Vous pouvez ensuite modifier ces scripts, créez chaque objet individuellement et même utiliser SQL Server Agent pour planifier la création de ces objets.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>À l’aide de SSMA pour synchroniser des objets avec SQL Server  
Pour utiliser SSMA pour créer des objets de base de données SQL Server, vous sélectionnez les objets dans l’Explorateur de métadonnées SQL Server et synchronisez ensuite les objets avec SQL Server, comme indiqué dans la procédure suivante. Par défaut, si les objets existent déjà dans SQL Server, et si les métadonnées SSMA sont plus récente que l’objet dans SQL Server, SSMA modifier les définitions d’objets dans SQL Server. Vous pouvez modifier le comportement par défaut en modifiant **paramètres du projet**.  
  
> [!NOTE]  
> Vous pouvez sélectionner les objets de base de données SQL Server existants qui n’ont pas été converties à partir de bases de données Oracle. Toutefois, ces objets ne seront pas recréés ou modifiés par SSMA.  
  
**Pour synchroniser des objets avec SQL Server**  
  
1.  Dans l’Explorateur de métadonnées SQL Server, développez le nœud supérieur de SQL Server, puis puis **bases de données**.  
  
2.  Sélectionnez les objets à traiter :  
  
    -   Pour synchroniser une base de données complète, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour synchroniser ou omettre des objets individuels ou des catégories d’objets, activez ou désactivez la case à cocher en regard de l’objet ou un dossier.  
  
3.  Une fois que vous avez sélectionné les objets à traiter dans l’Explorateur de métadonnées SQL Server, cliquez sur **bases de données**, puis cliquez sur **synchroniser avec la base de données**.  
  
    Vous pouvez également synchroniser des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **synchroniser avec la base de données**.  
  
    Après cela, SSMA affichera le **synchroniser avec la base de données** boîte de dialogue, où vous pouvez voir les deux groupes d’éléments. Sur le côté gauche, SSMA affiche les objets de base de données sélectionnée représentées dans une arborescence. Sur le côté droit, vous pouvez voir une arborescence représentant les mêmes objets dans les métadonnées SSMA. Vous pouvez développer l’arborescence en cliquant sur la droite ou gauche bouton « + ». La direction de la synchronisation est indiquée dans la colonne d’Action placée entre les deux arborescences.  
  
    Un signe de l’action peut être dans trois états :  
  
    -   Une flèche gauche signifie que le contenu de métadonnées est enregistré dans la base de données (la valeur par défaut).  
  
    -   Une flèche droite signifie le contenu de la base de données remplacent les métadonnées SSMA.  
  
    -   Une croix signifie qu'aucune action n’est entreprise.  
  
Cliquez sur le signe de l’action pour modifier l’état. Véritable synchronisation sera effectuée lorsque vous cliquez sur **OK** bouton de la **synchroniser avec la base de données** boîte de dialogue.  
  
## <a name="scripting-objects"></a>Objets de script  
Pour enregistrer [!INCLUDE[tsql](../../includes/tsql_md.md)] définitions des objets de base de données convertie, ou modifier les définitions d’objet et d’exécuter des scripts vous-même, vous pouvez enregistrer la base de données convertie définitions d’objet dans [!INCLUDE[tsql](../../includes/tsql_md.md)] scripts.  
  
**Pour enregistrer les objets en tant que scripts**  
  
1.  Avec le bouton droit une fois que vous avez sélectionné les objets à enregistrer dans un script, **bases de données**, puis cliquez sur **enregistrer en tant que Script**.  
  
    Vous pouvez également créer un script des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **enregistrer en tant que Script**.  
  
2.  Dans le **enregistrer en tant que** boîte de dialogue, recherchez le dossier où vous souhaitez enregistrer le script, entrez un nom de fichier dans le **nom de fichier** , puis cliquez sur OK SSMA permet d’ajouter l’extension de nom de fichier .sql.  
  
### <a name="modifying-scripts"></a>Modification des Scripts  
Une fois que vous avez enregistré les définitions d’objets SQL Server comme un ou plusieurs scripts, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] pour afficher et modifier les scripts.  
  
**Pour modifier un script**  
  
1.  Sur le [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Dans le **Open** boîte de dialogue, sélectionnez votre fichier de script, puis cliquez sur OK.
  
3.  Modifiez le fichier de script à l’aide de l’éditeur de requête.  
  
    Pour plus d’informations sur l’éditeur de requête, consultez « Éditeur de commandes et fonctionnalités pratiques » dans la documentation en ligne de SQL Server.  
  
4.  Pour enregistrer le script, dans, cliquez sur le menu fichier **enregistrer**.  
  
### <a name="running-scripts"></a>Exécution de Scripts  
Vous pouvez exécuter un script ou des instructions individuelles, en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Pour exécuter un script**  
  
1.  Sur le [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Dans le **Open** boîte de dialogue, sélectionnez votre fichier de script, puis cliquez sur OK  
  
3.  Pour exécuter le script complet, appuyez sur la **F5** clé.  
  
4.  Pour exécuter un ensemble d’instructions, les instructions select dans la fenêtre d’éditeur de requête, puis appuyez sur la **F5** clé.  
  
Pour plus d’informations sur l’utilisation de l’éditeur de requête pour exécuter des scripts, consultez «[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] requête » dans la documentation en ligne de SQL Server.  
  
Vous pouvez également exécuter des scripts à partir de la ligne de commande à l’aide de la **sqlcmd** utilitaire et à partir de l’Agent SQL Server. Pour plus d’informations sur **sqlcmd**, consultez « utilitaire sqlcmd » dans la documentation en ligne de SQL Server. Pour plus d’informations sur l’Agent SQL Server, consultez « Automating tâches administratives (Agent SQL Server) » dans la documentation en ligne de SQL Server.  
  
## <a name="securing-objects-in-sql-server"></a>Sécurisation des objets dans SQL Server  
Une fois que vous avez chargé les objets de base de données convertis dans SQL Server, vous pouvez accorder et refuser des autorisations sur ces objets. Il est judicieux de le faire avant de migrer des données dans SQL Server. Pour plus d’informations sur la façon de sécuriser les objets dans SQL Server, consultez « Sécurité considérations relatives à des bases de données et base de données des Applications » dans la documentation en ligne de SQL Server.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [migrer des données dans SQL Server](http://msdn.microsoft.com/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
