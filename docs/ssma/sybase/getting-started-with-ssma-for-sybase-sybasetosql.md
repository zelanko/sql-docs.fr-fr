---
title: Bien démarrer avec SSMA pour SAP ASE (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7e308589ab565b5702bbf2cba939835a50c08d8e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126629"
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>Bien démarrer avec SSMA pour SAP ASE (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour SAP ASE vous permet de rapidement convertir des schémas de base de données SAP Adaptive Server Enterprise (ASE) à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou schémas de base de données SQL Azure, téléchargez les schémas qui en résulte dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, et migrer des données à partir de SAP ASE pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
Cette rubrique présente le processus d’installation et permet de vous familiariser avec l’interface utilisateur SSMA.  
  
## <a name="installing-and-licensing-ssma"></a>Installation et la licence de SSMA  
Pour utiliser SSMA, vous devez d’abord installer le programme du client SSMA sur un ordinateur qui peut accéder à la fois l’instance de la source de SAP ASE et l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Pour utiliser la migration de données côté serveur, vous devez installer le pack d’extension et au moins un des fournisseurs de SAP ASE (OLE DB ou ADO.NET) sur l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces composants prennent en charge la migration des données et l’émulation des fonctions du système SAP ASE. Pour obtenir des instructions d’installation, consultez [l’installation de SSMA pour SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md).  
  
Pour démarrer SSMA, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant pour Sybase**, puis sélectionnez  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant pour Sybase**. La première fois que vous démarrez SSMA, une boîte de dialogue licence s’affiche. SSMA une licence à l’aide d’un identifiant Windows Live ID avant de pouvoir utiliser SSMA. Instructions de licence sont incluses dans les instructions d’installation dans le [l’installation de SSMA pour Sybase Client &#40;SybaseToSQL&#41; ](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) rubrique.  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA pour interface utilisateur de SAP ASE  
Une fois SSMA est installé et une licence, vous pouvez utiliser SSMA pour migrer des bases de données SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Cela permet de vous familiariser avec l’interface utilisateur SSMA avant de commencer. Le diagramme suivant illustre l’interface utilisateur de SSMA, y compris les explorateurs de métadonnées, métadonnées, barres d’outils, sortie et volet Liste d’erreur :  
  
![SSMA pour Interface utilisateur de l’ASE SAP](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA pour Interface utilisateur de l’ASE SAP")  
  
Pour démarrer une migration, vous devez d’abord créer un nouveau projet. Ensuite, vous vous connectez à SAP ASE. Après une connexion réussie, une hiérarchie de bases de données SAP ASE s’affiche dans l’Explorateur de métadonnées Sybase. Vous pouvez ensuite les objets avec le bouton droit dans l’Explorateur de métadonnées de Sybase pour effectuer des tâches telles que créent des rapports qui évaluent les conversions vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Vous pouvez également effectuer ces tâches via les menus et barres d’outils.  
  
Vous devez également connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Après une connexion réussie, une hiérarchie de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou bases de données SQL Azure figureront dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure. Après la conversion de schémas SAP ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou schémas de base de données SQL Azure, sélectionnez ces schémas convertis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure, puis charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
Après avoir chargé les schémas convertis en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de la base de données SQL Azure, vous pouvez revenir à l’Explorateur de métadonnées Sybase et migrer des données à partir de bases de données SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou bases de données SQL Azure.  
  
Pour plus d’informations sur ces tâches et comment les exécuter, consultez [migration SAP ASE bases de données vers SQL Server - Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md).  
  
Les sections suivantes décrivent les fonctionnalités de l’interface utilisateur SSMA.  
  
### <a name="metadata-explorers"></a>Explorateurs de métadonnées  
SSMA contient deux explorateurs de métadonnées pour rechercher et effectuer des actions sur SAP ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou bases de données SQL Azure.  
  
#### <a name="sybase-metadata-explorer"></a>Explorateur de métadonnées Sybase  
Explorateur de métadonnées Sybase affiche des informations sur les bases de données sur l’instance de la source de SAP ASE.  
  
À l’aide de l’Explorateur de métadonnées Sybase, vous pouvez effectuer les tâches suivantes :  
  
-   Parcourir les tables dans chaque base de données.  
  
-   Sélectionner des objets pour la conversion et puis de convertir les objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe de base de données SQL Azure. Pour plus d’informations, consultez [conversion des objets de base de données SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
-   Sélectionner des objets pour la migration de données, puis migrer les données à partir de ces objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Pour plus d’informations, consultez [migration de données ASE SAP vers SQL Server - Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server ou l’Explorateur de métadonnées SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure affiche des informations sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Lorsque vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de la base de données SQL Azure, SSMA récupère les métadonnées relatives à cette instance et le stocke dans le fichier projet.  
  
Vous pouvez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure pour sélectionner des objets de base de données SAP ASE convertis, puis charger (synchronisation de) ces objets dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
Pour plus d’informations, consultez [le chargement des objets de base de données convertis dans SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md).  
  
### <a name="metadata"></a>Métadonnées  
À droite de chaque Explorateur de métadonnées des onglets qui décrivent l’objet sélectionné. Par exemple, si vous sélectionnez une table dans l’Explorateur de métadonnées de Sybase, six onglets s’affichent : **Table**, **SQL**, **mappage de Type**, **données**, **propriétés**, et **rapport**. Le **rapport** onglet contient des informations uniquement après avoir créé un rapport contenant l’objet sélectionné. Si vous sélectionnez une table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure, trois onglets s’affichent : **Table**, **SQL**, et **données**.  
  
La plupart des paramètres de métadonnées sont en lecture seule. Toutefois, vous pouvez modifier les métadonnées suivantes :  
  
-   Dans l’Explorateur de métadonnées de Sybase, vous pouvez modifier les procédures et mappages de type. Apportez ces modifications avant de convertir des schémas.  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure, vous pouvez modifier le [!INCLUDE[tsql](../../includes/tsql-md.md)] pour les procédures stockées. Apportez ces modifications avant de charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Modifications apportées dans l’Explorateur de métadonnées sont répercutées dans les métadonnées du projet, pas dans les bases de données source ou cible.  
  
### <a name="toolbars"></a>Barres d'outils  
SSMA a deux barres d’outils : une barre d’outils du projet et une barre d’outils de migration.  
  
#### <a name="the-project-toolbar"></a>La barre d’outils du projet  
La barre d’outils du projet contient des boutons pour l’utilisation de projets, la connexion à SAP ASE et la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Ces boutons se présenter comme les commandes sur le **fichier** menu.  
  
#### <a name="the-migration-toolbar"></a>La barre d’outils de Migration  
La barre d’outils de migration contient les commandes suivantes :  
  
|Bouton|Fonction|  
|----------|------------|  
|**Créer des rapports**|Convertit les objets sélectionnés de SAP ASE vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, puis crée un rapport qui indique le succès de la conversion a.<br /><br />Cette commande est disponible uniquement lorsque les objets sont sélectionnés dans l’Explorateur de métadonnées Sybase.|  
|**Convertir le schéma**|Convertit les objets sélectionnés de SAP ASE vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de base de données SQL Azure.<br /><br />Cette commande est disponible uniquement lorsque les objets sont sélectionnés dans l’Explorateur de métadonnées Sybase.|  
|**Migrer des données**|Migre les données à partir de la base de données SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Avant d’exécuter cette commande, vous devez convertir les schémas SAP ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas de base de données SQL Azure, puis charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.<br /><br />Cette commande est disponible uniquement lorsque les objets sont sélectionnés dans l’Explorateur de métadonnées Sybase.|  
|**Arrêter**|Arrête le processus actuel, telles que la conversion des objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe de base de données SQL Azure.|  
  
### <a name="menus"></a>Menus  
SSMA contient les menus suivants :  
  
|Menu|Description|  
|--------|---------------|  
|**Fichier**|Contient des commandes pour travailler avec des projets, la connexion à SAP ASE et la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.|  
|**Modifier**|Contient des commandes pour la recherche et de travailler avec du texte dans les pages de détails, telles que la copie [!INCLUDE[tsql](../../includes/tsql-md.md)] depuis le volet de détails SQL. Contient également le **gérer les signets** option, où vous pouvez voir une liste de signets existants. Vous pouvez utiliser les boutons sur le côté droit de la boîte de dialogue pour gérer les signets.|  
|**Affichage**|Contient le **synchroniser les explorateurs de métadonnées** commande. Cette opération synchronise les objets entre l’Explorateur de métadonnées Sybase et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure. Contient également des commandes pour afficher et masquer le **sortie** et **liste d’erreurs** volets et une option **dispositions** pour gérer les dispositions.|  
|**Outils**|Contient des commandes pour créer des rapports, exporter des données et migrer des objets et données. Permet également d’accéder à la **paramètres globaux** et **paramètres du projet** boîtes de dialogue.|  
|**Testeur**|Contient des commandes pour créer des cas de test, afficher les résultats de test et commandes de gestion des sauvegardes de base de données.|  
|**Aide**|Fournit l’accès à l’aide de SSMA et en le **sur** boîte de dialogue.|  
  
### <a name="output-pane-and-error-list-pane"></a>Volets de sortie et liste d’erreurs  
Le **vue** menu fournit des commandes pour activer/désactiver la visibilité du volet sortie et le volet de la liste d’erreurs :  
  
-   Le volet de sortie affiche les messages d’état à partir de SSMA pendant la conversion des objets, la synchronisation de l’objet et la migration des données.  
  
-   Le volet de liste d’erreurs affiche les messages d’erreur, avertissement et d’information dans une liste que vous pouvez trier.  
  
## <a name="see-also"></a>Voir aussi  
[Migration SAP ASE bases de données SQL Server - Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Référence de l’Interface utilisateur &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
