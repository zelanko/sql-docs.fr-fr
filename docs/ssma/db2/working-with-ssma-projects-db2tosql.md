---
title: Utilisation de projets SSMA (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 07abef8a-28e8-4a66-927c-c9a5b8c938ef
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d2c585764e5bb7fffa55624054aecc7a4c589bbe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086178"
---
# <a name="working-with-ssma-projects-db2tosql"></a>Utilisation de projets SSMA (DB2ToSQL)
Pour migrer des bases de données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous créez tout d’abord un projet SSMA. Le projet est un fichier qui contient les informations suivantes :  
  
-   Les métadonnées sur les bases de données DB2 que vous souhaitez migrer vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Métadonnées relatives à l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui recevra les objets migrés et les données.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informations de connexion.  
  
-   Paramètres du projet.  
  
Lorsque vous ouvrez un projet, il est déconnecté de DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Qui vous permet de travailler hors connexion. Pour plus d’informations sur la reconnexion au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [connexion à SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Examen des paramètres de projet par défaut  
SSMA contient plusieurs paramètres pour la conversion et chargement d’objets de base de données, migration de données et synchronisation de SSMA avec DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les paramètres par défaut sont appropriés pour de nombreux utilisateurs. Toutefois, avant de créer un nouveau projet SSMA, vous devez examiner les paramètres. Si vous le souhaitez, vous pouvez modifier les paramètres par défaut qui seront utilisés pour vos nouveaux projets.  
  
**Pour passer en revue les paramètres de projet par défaut**  
  
1.  Sur le **outils** menu, cliquez sur **par défaut des paramètres de projet**.  
  
2.  Sélectionnez le type de projet dans **Version cible de Migration** liste déroulante pour les paramètres sont requis pour être affichées ou modifiées, puis cliquez sur **général** onglet.  
  
3.  Dans le volet gauche, cliquez sur **Conversion**.  
  
4.  Dans le volet droit, passez en revue et modifier les paramètres en fonction des besoins. Pour plus d’informations sur ces paramètres, consultez [paramètres du projet &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
5.  Répétez les étapes 1 à 3 pour les pages de la Migration, la synchronisation, le chargement des objets système, l’interface graphique utilisateur et le mappage de Type.  
  
    -   Pour plus d’informations sur les paramètres de migration, consultez [paramètres du projet &#40;Migration&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres d’objet système, consultez [paramètres du projet&#40;chargement d’objets système&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-loading-system-objects-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de la synchronisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [paramètres du projet&#40;synchronisation&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de l’interface graphique utilisateur, consultez [paramètres du projet &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de mappage de type de données, consultez [paramètres du projet &#40;mappage de Type&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="creating-new-projects"></a>Création de projets  
Pour migrer des données à partir de bases de données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez d’abord créer un projet.  
  
**Pour créer un projet**  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
    La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Dans la zone **Nom** , tapez le nom de votre projet.  
  
3.  Dans le **emplacement** zone, entrez ou sélectionnez un dossier pour le projet, puis cliquez sur **OK**.  
  
4.  Dans le **à la Migration** liste déroulante, sélectionnez la version du serveur cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la migration. Les options disponibles sont :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL DB  
  
## <a name="customizing-project-settings"></a>Personnalisation des paramètres de projet  
Outre la définition des paramètres de projet par défaut qui s’appliquent à tous les nouveaux projets SSMA, vous pouvez personnaliser les paramètres pour chaque projet. Pour plus d’informations, consultez [définition des Options de projet &#40;OracleToSQL&#41; ](../../ssma/oracle/setting-project-options-oracletosql.md) et rubriques connexes.  
  
Lorsque vous personnalisez les mappages de types de données entre bases de données source et cible, vous pouvez définir des mappages pour le projet, la base de données ou le niveau de l’objet. Pour plus d’informations, consultez [DB2 de mappage et les Types de données SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
## <a name="saving-projects"></a>Enregistrement des projets  
Lorsque vous enregistrez un projet, SSMA conserve les paramètres du projet et éventuellement les métadonnées de la base de données, dans le fichier projet.  
  
**Pour enregistrer un projet**  
  
-   Sur le **fichier** menu, cliquez sur **enregistrer le projet**.  
  
    Si les schémas du projet ont été modifiées ou n’ont pas été converties, SSMA vous invitera à charger et enregistrer les métadonnées. Charger et enregistrer les métadonnées seront vous permettent de travailler hors connexion. Il vous permet également d’envoyer un fichier de projet complet à d’autres personnes, tels que du personnel de support technique. Si vous êtes invité à enregistrer les métadonnées, procédez comme suit :  
  
    1.  Pour chaque schéma que présente l’état de **métadonnées manquantes**, sélectionnez la case à cocher en regard du nom de la base de données.  
  
        L’enregistrement des métadonnées peut prendre plusieurs minutes. Si vous ne souhaitez pas enregistrer les métadonnées, ne sélectionnez pas les cases à cocher.  
  
    2.  Cliquez sur le bouton **Enregistrer**.  
  
        SSMA analysera les schémas DB2 et enregistrer les métadonnées dans le fichier projet.  
  
## <a name="opening-projects"></a>Ouverture de projets  
Lorsque vous ouvrez un projet, il est déconnecté à partir de DB2 et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Qui vous permet de travailler hors connexion. Pour mettre à jour des métadonnées, charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour migrer des données, vous devez vous reconnecter à DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Pour ouvrir un projet**  
  
1.  Utilisez une des procédures suivantes :  
  
    -   Sur le **fichier** menu, pointez sur **projets récents**, puis cliquez sur le projet que vous souhaitez ouvrir.  
  
    -   Sur le **fichier** menu, sélectionnez **ouvrir un projet**, recherchez le fichier de projet .o2ssproj, sélectionnez le fichier, puis cliquez sur **Open**.  
  
2.  Pour vous reconnecter à DB2, sur le **fichier** menu, cliquez sur **reconnexion à DB2**.  
  
3.  Pour vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dans le **fichier** menu, cliquez sur **reconnexion à SQL Server**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [connexion à la base de données DB2](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
[Connexion à la base de données DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
[Connexion à SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
  
