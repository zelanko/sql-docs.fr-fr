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
ms.openlocfilehash: eb6f035b4d597e2b648134c195b698554dc78e12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68072467"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Utilisation de projets SSMA (SybaseToSQL)
Pour migrer des bases de données Sybase Adaptive Server Enterprise ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ASE) vers ou SQL Azure, vous devez d’abord créer un projet SSMA. Le projet est un fichier qui contient des métadonnées sur les bases de données ASE que vous souhaitez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] migrer vers ou SQL Azure, des métadonnées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l’instance cible de ou SQL Azure qui recevront les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les données migrés, ou SQL Azure des informations de connexion et des paramètres de projet.  
  
Lorsque vous ouvrez un projet, il est déconnecté de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Cela vous permet de travailler hors connexion. Vous pouvez vous reconnecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à ou SQL Azure. Pour plus d’informations, consultez [connexion à SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  /  [connexion à Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Vérification des paramètres de projet par défaut  
SSMA contient plusieurs options pour convertir et charger des objets de base de données, migrer des données et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] synchroniser SSMA avec ASE et ou SQL Azure. Les paramètres par défaut de ces options conviennent à de nombreux utilisateurs. Toutefois, avant de créer un nouveau projet SSMA, vous devez passer en revue les options et, si vous le souhaitez, modifier les valeurs par défaut qui seront utilisées pour tous vos nouveaux projets.  
  
**Pour examiner les paramètres de projet par défaut**  
  
1.  Dans le menu **Outils** , sélectionnez **paramètres du projet par défaut**.  
  
2.  Sélectionnez le type de projet dans la liste déroulante **version cible** de la migration pour laquelle vous devez afficher ou modifier les paramètres, puis cliquez sur l’onglet **général** .  
  
3.  Dans le volet gauche, cliquez sur **conversion**.  
  
4.  Dans le volet droit, passez en revue les options, en modifiant les options selon vos besoins. Pour plus d’informations sur ces options, consultez [Project settings &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Répétez les étapes 1-3 pour la migration, les SQL Azure, le chargement d’objets, l’interface graphique utilisateur et les pages de mappage de type.  
  
    -   Pour plus d’informations sur les options de migration, consultez [Project settings &#40;migration&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Pour plus d’informations sur les options de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]chargement d’objets dans, consultez [paramètres du projet &#40;synchronisation&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Pour plus d’informations sur les options d’interface utilisateur graphique, consultez [paramètres du projet &#40;interface utilisateur graphique&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Pour plus d’informations sur les paramètres de mappage de type de données, cliquez sur [paramètres du projet &#40;mappage de type&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Pour plus d’informations sur les options de SQL Azure, consultez [paramètres du projet &#40;base de données SQL Azure &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Les paramètres de SQL Azure s’affichent uniquement lorsque vous sélectionnez **migration vers SQL Azure lors de** la création d’un projet.  
  
## <a name="creating-new-projects"></a>Création de projets  
Pour migrer des données de bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données ASE vers ou SQL Azure, vous devez d’abord créer un projet.  
  
**Pour créer un projet**  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau projet**.  
  
    La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Dans la zone **Nom** , tapez le nom de votre projet.  
  
3.  Dans la zone **emplacement** , entrez ou sélectionnez un dossier pour le projet.  
  
4.  Dans la liste déroulante **migration vers** , sélectionnez la version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la cible utilisée pour la migration. Voici les options disponibles :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL DB  
  
Puis cliquez sur **OK**.  
  
## <a name="customizing-project-settings"></a>Personnalisation des paramètres du projet  
En plus de définir les paramètres de projet par défaut qui s’appliquent à tous les nouveaux projets SSMA, vous pouvez personnaliser les paramètres de chaque projet. Pour plus d’informations, consultez [définition des options de projet &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
Lorsque vous personnalisez des mappages de types de données entre des bases de données source et cible, vous pouvez définir des mappages au niveau du projet, de la base de données ou de l’objet. Pour plus d’informations sur le mappage de type, consultez [mappage des types de données Sybase ASE et SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Enregistrement des projets  
Lorsque vous enregistrez un projet, SSMA conserve les paramètres du projet et éventuellement les métadonnées de la base de données dans le fichier projet.  
  
**Pour enregistrer un projet**  
  
-   Dans le menu **fichier** , sélectionnez **enregistrer le projet**.  
  
    Si les bases de données dans le projet ont été modifiées ou n’ont pas été converties, SSMA vous invite à enregistrer les métadonnées dans le projet. L’enregistrement des métadonnées vous permet de travailler hors connexion et d’envoyer un fichier projet complet à d’autres personnes, y compris le personnel de support technique. Si vous êtes invité à enregistrer les métadonnées, procédez comme suit :  
  
    1.  Pour chaque base de données qui affiche l’état des **métadonnées manquantes**, activez la case à cocher en regard du nom de la base de données.  
  
        L’enregistrement des métadonnées peut prendre plusieurs minutes. Si vous ne souhaitez pas enregistrer les métadonnées à ce stade, n’activez pas les cases à cocher.  
  
    2.  Cliquez sur le bouton **Enregistrer**.  
  
        SSMA analyse les schémas de l’ASE Sybase et enregistre les métadonnées dans le fichier projet.  
  
## <a name="opening-projects"></a>Ouverture de projets  
Lorsque vous ouvrez un projet, il est déconnecté de l’ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de ou SQL Azure. Cela vous permet de travailler hors connexion. Pour mettre à jour les métadonnées, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargez des objets de base de données dans ou SQL Azure. Pour migrer des données, vous devez vous reconnecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à ASE et ou SQL Azure.  
  
**Pour ouvrir un projet**  
  
1.  Utilisez l’une des procédures suivantes :  
  
    -   Dans le menu **fichier** , pointez sur **projets récents**, puis sélectionnez le projet que vous souhaitez ouvrir.  
  
    -   Dans le menu **fichier** , sélectionnez **ouvrir un projet**, recherchez le fichier projet. s2ssproj, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
2.  Pour vous reconnecter à ASE, dans le menu **fichier** , sélectionnez **se reconnecter à Sybase**.  
  
3.  Pour vous reconnecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à ou SQL Azure, dans le menu **fichier** , sélectionnez **se reconnecter pour SQL Server** / **se reconnecter à SQL Azure**.  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante du processus de migration consiste à [se connecter à Sybase ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Sybase ASE vers SQL Server-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Connexion à Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Connexion à SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Connexion à Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
