---
title: Utilisation de projets SSMA (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7e1be086b891d6888c6509b15adc6664b3022978
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187130"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Utilisation de projets SSMA (SybaseToSQL)
Pour migrer des bases de données Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous créez tout d’abord un projet SSMA. Le projet est un fichier qui contient des métadonnées sur les bases de données ASE que vous souhaitez migrer vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, les métadonnées sur l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure qui reçoit les objets migrés et les données, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure informations de connexion et les paramètres du projet.  
  
Lorsque vous ouvrez un projet, il est déconnecté [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Cela vous permet de travailler hors connexion. Vous pouvez vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Pour plus d’informations, consultez [connexion à SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [connexion à Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Examen des paramètres de projet par défaut  
SSMA contient plusieurs options de conversion et chargement d’objets de base de données, migration de données et la synchronisation de SSMA avec ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Les paramètres par défaut pour ces options conviennent pour de nombreux utilisateurs. Toutefois, avant de créer un nouveau projet SSMA, vous devez examiner les options et, si vous le souhaitez, modifiez les valeurs par défaut qui seront utilisés pour vos nouveaux projets.  
  
**Pour passer en revue les paramètres de projet par défaut**  
  
1.  Sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**.  
  
2.  Sélectionnez le type de projet dans **Version cible de Migration** liste déroulante pour les paramètres sont requis pour être affichées ou modifiées, puis cliquez sur **général** onglet.  
  
3.  Dans le volet gauche, cliquez sur **Conversion**.  
  
4.  Dans le volet droit, passez en revue les options de modification des options en fonction des besoins. Pour plus d’informations sur ces options, consultez [paramètres du projet &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Répétez les étapes 1 à 3 pour les pages de la Migration, SQL Azure, le chargement des objets, l’interface graphique utilisateur et le mappage de Type.  
  
    -   Pour plus d’informations sur les options de migration, consultez [paramètres du projet &#40;Migration&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Pour plus d’informations sur les options de chargement d’objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [paramètres du projet &#40;synchronisation&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Pour plus d’informations sur les options de l’interface graphique utilisateur, consultez [paramètres du projet &#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Pour plus d’informations sur les paramètres de mappage de type de données, cliquez sur [paramètres du projet &#40;mappage de Type&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Pour plus d’informations sur les options de SQL Azure, consultez [paramètres du projet &#40;Azure SQL DB &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Les paramètres de SQL Azure seront affichera uniquement lorsque vous sélectionnez **Migration vers SQL Azure** lors de la création d’un projet.  
  
## <a name="creating-new-projects"></a>Création de projets  
Pour migrer des données à partir de bases de données ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous devez d’abord créer un projet.  
  
**Pour créer un projet**  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau projet**.  
  
    La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Dans la zone **Nom** , tapez le nom de votre projet.  
  
3.  Dans le **emplacement** zone, entrez ou sélectionnez un dossier pour le projet.  
  
4.  Dans le **à la Migration** liste déroulante, sélectionnez la version du serveur cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la migration. Les options disponibles sont :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL DB  
  
Puis cliquez sur **OK**.  
  
## <a name="customizing-project-settings"></a>Personnalisation des paramètres de projet  
Outre la définition des paramètres de projet par défaut qui s’appliquent à tous les nouveaux projets SSMA, vous pouvez personnaliser les paramètres pour chaque projet. Pour plus d’informations, consultez [définition des Options de projet &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
Lorsque vous personnalisez les mappages de types de données entre bases de données source et cible, vous pouvez définir des mappages pour le projet, la base de données ou le niveau de l’objet. Pour plus d’informations sur le mappage de type, consultez [mappage Sybase ASE et Types de données SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Enregistrement des projets  
Lorsque vous enregistrez un projet, SSMA conserve les paramètres du projet et éventuellement les métadonnées de la base de données, dans le fichier projet.  
  
**Pour enregistrer un projet**  
  
-   Sur le **fichier** menu, sélectionnez **enregistrer le projet**.  
  
    Si les bases de données au sein du projet ont été modifiées ou n’ont pas été converties, SSMA vous invitera à enregistrer les métadonnées dans le projet. L’enregistrement des métadonnées vous permettra de travailler hors connexion et pour envoyer un fichier de projet complet à d’autres personnes, y compris le personnel de support technique. Si vous êtes invité à enregistrer les métadonnées, procédez comme suit :  
  
    1.  Pour chaque base de données qui affiche l’état **métadonnées manquantes**, sélectionnez la case à cocher en regard du nom de la base de données.  
  
        L’enregistrement des métadonnées peut prendre plusieurs minutes. Si vous ne souhaitez pas enregistrer les métadonnées à ce stade, ne sélectionnez pas les cases à cocher.  
  
    2.  Cliquez sur le bouton **Enregistrer**.  
  
        SSMA analysera les schémas Sybase ASE et enregistrer les métadonnées dans le fichier projet.  
  
## <a name="opening-projects"></a>Ouverture de projets  
Lorsque vous ouvrez un projet, il est déconnecté de l’ASE et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Cela vous permet de travailler hors connexion. Pour mettre à jour des métadonnées, charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Pour migrer des données, vous devez vous reconnecter à ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
**Pour ouvrir un projet**  
  
1.  Utilisez une des procédures suivantes :  
  
    -   Sur le **fichier** menu, pointez sur **projets récents**, puis sélectionnez le projet que vous souhaitez ouvrir.  
  
    -   Sur le **fichier** menu, sélectionnez **ouvrir un projet**, recherchez le fichier de projet .s2ssproj, sélectionnez le fichier, puis cliquez sur **Open**.  
  
2.  Pour vous reconnecter à ASE, sur le **fichier** menu, sélectionnez **reconnexion à Sybase**.  
  
3.  Pour vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, sur le **fichier** menu, sélectionnez **reconnexion à SQL Server** / **reconnexion à SQL Azure**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [se connecter à Sybase ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Connexion à Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Connexion à SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Connexion à la base de données SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
