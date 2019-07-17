---
title: Bien démarrer avec SQL Server Migration Assistant pour Access | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- error list pane
- getting started
- menus
- metadata explorers
- output pane
- toolbars
- user interface
- user interface overview
ms.assetid: 462a731f-08f1-44e1-9eeb-4deac6d2f6c5
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 863e62dc9e2970f7531bba15f7242c73c5b0f9e7
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68259927"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Bien démarrer avec l’Assistant Migration SQL Server pour l’accès (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour l’accès vous permet de convertir rapidement accéder aux objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de base de données SQL Azure, téléchargez les objets résultants dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, et migrer des données à partir de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Si nécessaire, vous pouvez également lier des tables de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou sur des tables de base de données SQL Azure afin que vous pouvez continuer à utiliser vos applications frontales Access existantes avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
Cette rubrique présente le processus d’installation et vous aide à vous familiariser avec l’interface utilisateur SSMA.  
  
## <a name="installing-ssma"></a>Installation de SSMA  
Pour utiliser SSMA, vous devez d’abord installer le programme du client SSMA sur un ordinateur qui peut accéder à la fois les bases de données à migrer et l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Pour obtenir des instructions d’installation, consultez [installation Assistant Migration SQL Server pour l’accès &#40;AccessToSQL&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Pour démarrer SSMA, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Assistant Migration SQL Server pour l’accès**, puis sélectionnez **migration vers SQL Server L’Assistant pour Access**.  
  
## <a name="using-ssma"></a>À l’aide de SSMA  
Après l’installation de SSMA, il est utile de vous familiariser avec l’interface utilisateur SSMA avant d’utiliser l’outil pour migrer des bases de données Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. L’interface utilisateur SSMA, y compris les explorateurs de métadonnées, métadonnées, barres d’outils, sortie et volet Liste d’erreur sont affichés dans le diagramme suivant :  
  
![SSMA pour Interface utilisateur graphique Access](../../ssma/access/media/ssmaforaccessgui.gif "SSMA pour Interface utilisateur graphique de l’accès")  
  
Pour démarrer une migration, créez un nouveau projet, puis ajoutez les bases de données Access à l’Explorateur de métadonnées d’accès. Vous pouvez ensuite cliquer sur les objets dans l’Explorateur de métadonnées d’accès pour effectuer des tâches telles que :
- Exportation d’un inventaire des objets de base de données Access à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.
- Création de rapports qui évaluent les conversions vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.
- Conversion de schémas d’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas de base de données SQL Azure.

Vous pouvez également effectuer ces tâches en utilisant les menus et barres d’outils.  
  
Vous devez également vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Après une connexion réussie, une hiérarchie de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données s’affiche dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées. Après la conversion de schémas d’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schémas, vous pouvez sélectionner ces schémas convertis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, puis charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Si vous avez sélectionné la base de données SQL Azure à partir de la migration sur la liste déroulante dans la boîte de dialogue Nouveau projet, vous devez vous connecter à la base de données SQL Azure. Après une connexion réussie, une hiérarchie de bases de données de base de données SQL Azure s’affiche dans l’Explorateur de métadonnées de base de données SQL Azure. Une fois que vous convertissez des schémas d’accès aux schémas de base de données SQL Azure, vous pouvez sélectionner ces schémas convertis dans l’Explorateur de métadonnées de base de données SQL Azure et puis charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Après avoir chargé les schémas convertis en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de la base de données SQL Azure, vous pouvez revenir à l’Explorateur de métadonnées d’accès et migrer des données à partir de bases de données Access dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou bases de données de base de données SQL Azure. Si nécessaire, vous pouvez également lier des tables de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des tables de base de données SQL Azure.  
  
Pour plus d’informations sur ces tâches et comment les exécuter, consultez les rubriques suivantes :  
  
-   [Préparation des bases de données Access pour la Migration](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Liaison d’Applications Access vers SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
Les sections suivantes décrivent les fonctionnalités de l’interface utilisateur SSMA.  
  
### <a name="metadata-explorers"></a>Explorateurs de métadonnées  
SSMA contient deux explorateurs de métadonnées que vous pouvez utiliser pour parcourir et effectuer des actions sur les accès et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou bases de données de base de données SQL Azure.  
  
#### <a name="access-metadata-explorer"></a>Accédez à l’Explorateur de métadonnées  
Explorateur de métadonnées d’accès affiche des informations sur les bases de données Access qui ont été ajoutés au projet. Lorsque vous ajoutez une base de données Access, SSMA récupère les métadonnées relatives à cette base de données, les métadonnées qui est disponible dans l’Explorateur de métadonnées d’accès.  
  
Vous pouvez utiliser l’Explorateur de métadonnées d’accès pour effectuer les tâches suivantes :  
  
-   Parcourir les tables dans chaque base de données Access.  
  
-   Sélectionner des objets pour la conversion et convertir les objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe. Pour plus d’informations, consultez [conversion des objets de base de données Access](converting-access-database-objects-accesstosql.md).  
  
-   Sélectionner des objets pour la migration de données et de migrer les données à partir de ces objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [migration d’accéder aux données dans SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Lier et supprimer le lien d’accès et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server ou l’Explorateur de métadonnées de base de données SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées de base de données SQL Azure affiche des informations sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Lorsque vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de la base de données SQL Azure, SSMA récupère les métadonnées relatives à cette instance et le stocke dans le fichier projet.  
  
Vous pouvez utiliser SQL Server ou l’Explorateur de métadonnées de base de données SQL Azure pour sélectionner des objets de base de données Access convertis et charger (synchronisation de) ces objets dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
Pour plus d’informations, consultez [le chargement des objets de base de données convertis dans SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Métadonnées  
À droite de chaque Explorateur de métadonnées des onglets qui décrivent l’objet sélectionné. Par exemple, si vous sélectionnez une table dans l’Explorateur de métadonnées d’accès, quatre onglets s’affichent : **Table**, **mappage de Type**, **propriétés**, et **données**. Si vous sélectionnez une table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, trois onglets s’affichent : **Table**, **SQL**, et **données**.  
  
La plupart des paramètres de métadonnées sont en lecture seule. Toutefois, vous pouvez modifier les métadonnées suivantes :  
  
-   Dans l’Explorateur de métadonnées d’accès, vous pouvez modifier les mappages de types. Veillez à effectuer ces modifications avant de créer des rapports ou convertir des schémas.  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, vous pouvez modifier les propriétés de table et d’index sur la **Table** onglet. Apportez ces modifications avant de charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [conversion des objets de base de données Access](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Barres d'outils  
SSMA a deux barres d’outils : une barre d’outils du projet et une barre d’outils de migration.  
  
#### <a name="the-project-toolbar"></a>La barre d’outils du projet  
La barre d’outils du projet contient des boutons pour l’utilisation de projets, l’ajout de fichiers de base de données Access et la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Ces boutons se présenter comme les commandes sur le **fichier** menu.  
  
#### <a name="the-migration-toolbar"></a>La barre d’outils de migration  
La barre d’outils de migration contient les commandes suivantes :  
  
|Bouton|Fonction|  
|----------|------------|  
|**Convertir, charger et migrer**|Convertit les bases de données Access, charge les objets convertis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, et migre les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB, tout en une seule étape.|  
|**Créer des rapports**|Convertit le schéma sélectionné accès [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe de base de données SQL Azure, puis crée un rapport qui indique le succès de la conversion a.<br /><br />Cette commande est disponible uniquement lorsque les objets sont sélectionnés dans l’Explorateur de métadonnées d’accès.|  
|**Convertir le schéma**|Convertit le schéma sélectionné accès [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas de base de données SQL Azure.<br /><br />Cette commande est disponible uniquement lorsque les objets sont sélectionnés dans l’Explorateur de métadonnées d’accès.|  
|**Migrer des données**|Migre les données à partir de la base de données Access à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Avant d’exécuter cette commande, vous devez convertir les schémas d’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas de base de données SQL Azure, puis charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.<br /><br />Cette commande est disponible uniquement lorsque les objets sont sélectionnés dans l’Explorateur de métadonnées d’accès.|  
|**Arrêter**|Arrête le processus actuel, telles que la conversion des objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe de base de données SQL Azure.|  
  
### <a name="menus"></a>Menus  
SSMA contient les menus suivants :  
  
|Menu|Description|  
|--------|---------------|  
|**File**|Contient des commandes pour l’Assistant de Migration, travaillez avec des projets, ajout et suppression des fichiers de base de données Access et la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.|  
|**Edition**|Contient des commandes pour la recherche et de travailler avec du texte dans les pages de détails, telles que la copie [!INCLUDE[tsql](../../includes/tsql-md.md)] depuis le volet de détails SQL. Pour ouvrir le **gérer les signets** boîte de dialogue, dans le menu Edition, cliquez sur Gérer les signets. Dans la boîte de dialogue, vous verrez une liste de signets existants. Vous pouvez utiliser les boutons sur le côté droit de la boîte de dialogue pour gérer les signets.|  
|**Affichage**|Contient le **synchroniser les explorateurs de métadonnées** commande. Cette opération synchronise les objets entre l’Explorateur de métadonnées d’accès et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l’Explorateur de métadonnées de base de données SQL Azure. Contient également des commandes pour afficher et masquer le **sortie** et **liste d’erreurs** volets et une option **dispositions** pour gérer les mises en page.|  
|**Outils**|Contient des commandes pour créer des rapports, exporter des données, migrer des objets et données, liez des tables et fournit des boîtes de dialogue Paramètres d’accès au déploiement global et projet.|  
|**Aide**|Fournit l’accès à l’aide de SSMA et en le **sur** boîte de dialogue.|  
  
### <a name="output-pane-and-error-list-pane"></a>Volets de sortie et liste d’erreurs  
Le **vue** menu fournit des commandes pour activer/désactiver la visibilité du volet sortie et le volet de la liste d’erreurs :  
  
-   Le volet de sortie affiche les messages d’état à partir de SSMA pendant la conversion des objets, la synchronisation de l’objet et la migration des données.  
  
-   Le volet de liste d’erreurs affiche les messages d’erreur, avertissement et d’information dans une liste que vous pouvez trier.  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
