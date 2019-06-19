---
title: Le chargement converti objets base de données dans SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 21962c8849204db6f3e5f114b6f8f86994d53b35
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298853"
---
# <a name="loading-converted-database-objects-into-sql-server-db2tosql"></a>Le chargement converti objets base de données dans SQL Server (DB2ToSQL)
Après avoir converti les schémas DB2 à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez charger les objets de base de données qui en résulte dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez avoir créer les objets SSMA, ou vous pouvez générer un script les objets et exécuter les scripts vous-même. En outre, SSMA vous permet de mettre à jour des métadonnées de la cible avec le contenu réel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Choix entre synchronisation et de Scripts  
Si vous souhaitez charger les objets de base de données convertie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans modification, vous pouvez avoir SSMA directement de créer ou de recréer les objets de base de données. Cette méthode est simple et rapide, mais ne permettent pas de personnaliser la [!INCLUDE[tsql](../../includes/tsql-md.md)] code qui définit le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets, autres que les procédures stockées.  
  
Si vous souhaitez modifier le [!INCLUDE[tsql](../../includes/tsql-md.md)] qui est utilisé pour créer des objets, ou si vous souhaitez davantage de contrôle sur la création d’objets, utilisez SSMA pour créer des scripts. Vous pouvez ensuite modifier ces scripts, créer chaque objet individuellement et même utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour planifier la création de ces objets.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>À l’aide de SSMA pour synchroniser des objets avec SQL Server  
Utilisation de SSMA pour créer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets de base de données, vous sélectionnez les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, puis de synchroniser les objets avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme illustré dans la procédure suivante. Par défaut, si les objets existent déjà dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et si les métadonnées SSMA sont plus récente que l’objet dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA modifiera les définitions d’objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez modifier le comportement par défaut en modifiant **paramètres du projet**.  
  
> [!NOTE]  
> Vous pouvez sélectionner existant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données des objets qui n’ont pas été converties à partir de bases de données DB2. Toutefois, ces objets ne seront pas recréés ou modifiés par SSMA.  
  
**Pour synchroniser des objets avec SQL Server**  
  
1.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, développez haut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nœud, puis développez **bases de données**.  
  
2.  Sélectionnez les objets à traiter :  
  
    -   Pour synchroniser une base de données complète, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour synchroniser ou omettre des objets individuels ou des catégories d’objets, activez ou désactivez la case à cocher en regard de l’objet ou un dossier.  
  
3.  Une fois que vous avez sélectionné les objets à traiter dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées avec le bouton droit **bases de données**, puis cliquez sur **synchroniser avec la base de données**.  
  
    Vous pouvez également synchroniser des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **synchroniser avec la base de données**.  
  
    Après cela, SSMA affichera le **synchroniser avec la base de données** boîte de dialogue, où vous pouvez voir les deux groupes d’éléments. Sur le côté gauche, SSMA affiche les objets de base de données sélectionnée représentées dans une arborescence. Sur le côté droit, vous pouvez voir une arborescence représentant les mêmes objets dans les métadonnées SSMA. Vous pouvez développer l’arborescence en cliquant sur la droite ou gauche bouton « + ». La direction de la synchronisation est indiquée dans la colonne d’Action placée entre les deux arborescences.  
  
    Un signe de l’action peut être dans trois états :  
  
    -   Une flèche gauche signifie que le contenu de métadonnées est enregistré dans la base de données (la valeur par défaut).  
  
    -   Une flèche droite signifie le contenu de la base de données remplacent les métadonnées SSMA.  
  
    -   Une croix signifie qu'aucune action n’est entreprise.  
  
Cliquez sur le signe de l’action pour modifier l’état. Véritable synchronisation sera effectuée lorsque vous cliquez sur **OK** bouton de la **synchroniser avec la base de données** boîte de dialogue.  
  
## <a name="scripting-objects"></a>Objets de script  
Pour enregistrer [!INCLUDE[tsql](../../includes/tsql-md.md)] définitions des objets de base de données convertie, ou modifier les définitions d’objet et d’exécuter des scripts vous-même, vous pouvez enregistrer la base de données convertie définitions d’objet dans [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.  
  
**Pour enregistrer les objets en tant que scripts**  
  
1.  Avec le bouton droit une fois que vous avez sélectionné les objets à enregistrer dans un script, **bases de données**, puis cliquez sur **enregistrer en tant que Script**.  
  
    Vous pouvez également créer un script des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en cliquant sur **enregistrer en tant que Script**.  
  
2.  Dans le **Enregistrer sous** boîte de dialogue, recherchez le dossier où vous souhaitez enregistrer le script, entrez un nom de fichier dans le **nom de fichier** boîte, puis [!INCLUDE[clickOK](../../includes/clickok-md.md)]. SSMA permet d’ajouter l’extension de nom de fichier .sql.  
  
### <a name="modifying-scripts"></a>Modification des Scripts  
Une fois que vous avez enregistré le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définitions d’objet en tant qu’un ou plusieurs scripts, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour afficher et modifier les scripts.  
  
**Pour modifier un script**  
  
1.  Sur le [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Dans le **Open** boîte de dialogue, sélectionnez votre fichier de script, puis cliquez sur OK.
  
3.  Modifiez le fichier de script à l’aide de l’éditeur de requête.  
  
    Pour plus d’informations sur l’éditeur de requête, consultez « Éditeur de commandes et fonctionnalités pratiques » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
4.  Pour enregistrer le script, dans, cliquez sur le menu fichier **enregistrer**.  
  
### <a name="running-scripts"></a>Exécution de Scripts  
Vous pouvez exécuter un script ou des instructions individuelles, en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Pour exécuter un script**  
  
1.  Sur le [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Dans le **Open** boîte de dialogue, sélectionnez votre fichier de script, puis [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  Pour exécuter le script complet, appuyez sur la **F5** clé.  
  
4.  Pour exécuter un ensemble d’instructions, les instructions select dans la fenêtre d’éditeur de requête, puis appuyez sur la **F5** clé.  
  
Pour plus d’informations sur l’utilisation de l’éditeur de requête pour exécuter des scripts, consultez « [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] requête » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
Vous pouvez également exécuter des scripts à partir de la ligne de commande à l’aide de la **sqlcmd** utilitaire et à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Pour plus d’informations sur **sqlcmd**, consultez « utilitaire sqlcmd » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, voir « Automatisation des tâches d’administration ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent) » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="securing-objects-in-sql-server"></a>Sécurisation des objets dans SQL Server  
Une fois que vous avez chargé les objets de base de données convertie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez accorder et refuser des autorisations sur ces objets. Il est judicieux de le faire avant de migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la sécurisation des objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez « Sécurité considérations relatives à des bases de données et base de données des Applications » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [migration de données DB2 dans SQL Server](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
## <a name="see-also"></a>Voir aussi  
[Migration de données DB2 dans SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
