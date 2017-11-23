---
title: Utilisation de projets SSMA (DB2ToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 07abef8a-28e8-4a66-927c-c9a5b8c938ef
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e82224e43147b5812a570f909f9a5a33c5585a6f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="working-with-ssma-projects-db2tosql"></a>Utilisation de projets SSMA (DB2ToSQL)
Pour migrer des bases de données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vous créez un projet SSMA. Le projet est un fichier qui contient les informations suivantes :  
  
-   Les métadonnées sur les bases de données DB2 que vous souhaitez migrer vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Métadonnées relatives à l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qui recevront les objets migrés et les données.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]informations de connexion.  
  
-   Paramètres du projet.  
  
Lorsque vous ouvrez un projet, il est déconnecté de DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Qui vous permet de travailler en mode hors connexion. Pour plus d’informations sur la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], consultez [la connexion à SQL Server &#40; DB2eToSQL &#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Examen des paramètres de projet par défaut  
SSMA contient plusieurs paramètres de conversion et le chargement des objets de base de données, de migration des données et synchronisation SSMA avec DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Les paramètres par défaut sont adaptés à de nombreux utilisateurs. Toutefois, avant de créer un nouveau projet SSMA, vous devez examiner les paramètres. Si vous le souhaitez, vous pouvez modifier les paramètres par défaut qui seront utilisés pour tous les nouveaux projets.  
  
**Pour passer en revue les paramètres de projet par défaut**  
  
1.  Sur le **outils** menu, cliquez sur **les paramètres de projet par défaut**.  
  
2.  Sélectionnez le type de projet dans **Version cible de la Migration** la liste déroulante pour les paramètres sont requis pour être affichées ou modifiées, puis cliquez sur **général** onglet.  
  
3.  Dans le volet gauche, cliquez sur **Conversion**.  
  
4.  Dans le volet droit, vérifiez et modifiez les paramètres selon vos besoins. Pour plus d’informations sur ces paramètres, consultez [paramètres du projet &#40; Conversion de &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
5.  Répétez les étapes 1 à 3 pour les pages de la Migration, la synchronisation, le chargement des objets système, l’interface graphique utilisateur et le mappage de Type.  
  
    -   Pour plus d’informations sur les paramètres de migration, consultez [paramètres du projet &#40; Migration &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-migration-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de l’objet système, consultez [paramètres du projet &#40; Chargement des objets système &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-loading-system-objects-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de synchronisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], consultez [paramètres du projet &#40; Synchronisation &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de l’interface graphique utilisateur, consultez [paramètres du projet &#40; L’interface graphique utilisateur &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-gui-db2tosql.md).  
  
    -   Pour plus d’informations sur les paramètres de mappage de type de données, consultez [paramètres du projet &#40; Mappage de type &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="creating-new-projects"></a>Création de projets  
Pour migrer des données à partir de bases de données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vous devez d’abord créer un projet.  
  
**Pour créer un projet**  
  
1.  Sur le **fichier** menu, cliquez sur **nouveau projet**.  
  
    La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Dans la zone **Nom** , tapez le nom de votre projet.  
  
3.  Dans le **emplacement** zone, entrez ou sélectionnez un dossier pour le projet, puis cliquez sur **OK**.  
  
4.  Dans le **à la Migration** liste déroulante, sélectionnez la version de la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilisé pour la migration. Les options disponibles sont :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   Base de données SQL Azure  
  
## <a name="customizing-project-settings"></a>Personnalisation des paramètres de projet  
Outre la définition des paramètres de projet par défaut qui s’appliquent à tous les nouveaux projets SSMA, vous pouvez personnaliser les paramètres pour chaque projet. Pour plus d’informations, consultez [définition des Options de projet &#40; OracleToSQL &#41;](../../ssma/oracle/setting-project-options-oracletosql.md) et rubriques connexes.  
  
Lorsque vous personnalisez les mappages de types de données entre bases de données source et cible, vous pouvez définir des mappages pour le projet, la base de données ou le niveau de l’objet. Pour plus d’informations, consultez [DB2 de mappage et les Types de données SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
## <a name="saving-projects"></a>L’enregistrement de projets  
Lorsque vous enregistrez un projet, SSMA conserve les paramètres du projet et éventuellement les métadonnées de la base de données, dans le fichier projet.  
  
**Pour enregistrer un projet**  
  
-   Sur le **fichier** menu, cliquez sur **enregistrer le projet**.  
  
    Si les schémas du projet ont été modifiées ou n’ont pas été converties, SSMA vous invitera à charger et enregistrer les métadonnées. Charger et enregistrer les métadonnées seront vous permettent de travailler hors connexion. Il vous permet également d’envoyer un fichier projet à d’autres personnes, tels que les membres du support technique. Si vous êtes invité à enregistrer les métadonnées, procédez comme suit :  
  
    1.  Pour chaque schéma que présente l’état de **métadonnées manquantes**, activez la case à cocher en regard du nom de la base de données.  
  
        L’enregistrement des métadonnées peut prendre plusieurs minutes. Si vous ne souhaitez pas enregistrer les métadonnées, ne sélectionnez pas les cases à cocher.  
  
    2.  Cliquez sur le **enregistrer** bouton.  
  
        SSMA analysera les schémas de DB2 et enregistrer les métadonnées dans le fichier projet.  
  
## <a name="opening-projects"></a>Ouverture de projets  
Lorsque vous ouvrez un projet, il est déconnecté à partir de DB2 et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Qui vous permet de travailler en mode hors connexion. Pour mettre à jour les métadonnées, charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Pour migrer des données, vous devez vous reconnecter à DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Pour ouvrir un projet**  
  
1.  Utilisez une des procédures suivantes :  
  
    -   Sur le **fichier** menu, pointez sur **projets récents**, puis cliquez sur le projet que vous souhaitez ouvrir.  
  
    -   Sur le **fichier** menu, sélectionnez **ouvrir le projet**, recherchez le fichier de projet .o2ssproj, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
2.  Se reconnecter à DB2, sur le **fichier** menu, cliquez sur **se reconnecter à DB2**.  
  
3.  Pour vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], dans le **fichier** menu, cliquez sur **se reconnecter à SQL Server**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [la connexion à la base de données DB2](http://msdn.microsoft.com/en-us/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de DB2 pour SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
[Connexion à la base de données DB2 &#40; DB2ToSQL &#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
[Connexion à SQL Server &#40; DB2eToSQL &#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
  
