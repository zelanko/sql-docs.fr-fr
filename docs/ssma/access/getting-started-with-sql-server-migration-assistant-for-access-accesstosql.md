---
title: Prise en main de Assistant Migration SQL Server pour l’accès | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68259927"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Prise en main de Assistant Migration SQL Server pour Access (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Assistant Migration (SSMA) pour Access vous permet de convertir rapidement des objets de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données Access en objets ou Azure SQL dB, de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charger les objets résultants dans ou Azure SQL dB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puis de migrer des données d’accès à ou à Azure SQL db. Si nécessaire, vous pouvez également lier des tables d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès à des tables ou à Azure SQL DB afin de pouvoir continuer à utiliser vos applications frontales Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existantes avec ou Azure SQL db.  
  
Cette rubrique présente le processus d’installation et vous aide à vous familiariser avec l’interface utilisateur SSMA.  
  
## <a name="installing-ssma"></a>Installation de SSMA  
Pour utiliser SSMA, vous devez d’abord installer le programme client SSMA sur un ordinateur qui peut accéder aux bases de données que vous souhaitez migrer et à l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance cible de ou à la base de données SQL Azure. Pour obtenir des instructions d’installation, consultez [installation de Assistant Migration SQL Server pour Access &#40;AccessToSQL&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Pour démarrer SSMA, cliquez sur **Démarrer**, pointez sur **tous les programmes**, sur **Assistant Migration SQL Server pour accès**, puis sélectionnez **Assistant Migration SQL Server pour l’accès**.  
  
## <a name="using-ssma"></a>Utilisation de SSMA  
Après l’installation de SSMA, vous pouvez vous familiariser avec l’interface utilisateur SSMA avant d’utiliser l’outil pour migrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des bases de données Access vers ou Azure SQL db. L’interface utilisateur SSMA, y compris les explorateurs de métadonnées, les métadonnées, les barres d’outils, le volet de sortie et le volet Liste d’erreurs, sont affichées dans le diagramme suivant :  
  
![SSMA pour l'interface d'utilisateur d'accès graphique](../../ssma/access/media/ssmaforaccessgui.gif "SSMA pour l'interface d'utilisateur d'accès graphique")  
  
Pour démarrer une migration, créez un projet, puis ajoutez des bases de données Access pour accéder à l’Explorateur de métadonnées. Vous pouvez ensuite cliquer avec le bouton droit sur objets dans l’Explorateur de métadonnées Access pour effectuer des tâches telles que :
- Exportation d’un inventaire des objets de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données Access vers ou Azure SQL db.
- Création de rapports qui évaluent les conversions vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL db.
- Conversion de schémas d’accès [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à ou de schémas Azure SQL db.

Vous pouvez également effectuer ces tâches à l’aide des barres d’outils et des menus.  
  
Vous devez également vous connecter à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Une fois la connexion établie, une hiérarchie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’affiche dans l’Explorateur de métadonnées. Après avoir converti les schémas d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès en schémas, vous pouvez sélectionner ces schémas convertis dans l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, puis charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Si vous avez sélectionné base de donnée SQL Azure dans la boîte de dialogue migrer vers la liste déroulante dans le nouveau projet, vous devez vous connecter à Azure SQL DB. Une fois la connexion établie, une hiérarchie de bases de données Azure SQL DB s’affiche dans l’Explorateur de métadonnées Azure SQL DB. Après avoir converti les schémas d’accès en schémas Azure SQL DB, vous pouvez sélectionner ces schémas convertis dans l’Explorateur de métadonnées Azure SQL DB, puis charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Une fois que vous avez chargé les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schémas convertis dans ou Azure SQL dB, vous pouvez revenir à l’Explorateur de métadonnées Access et migrer les données à partir des bases de données Access vers ou vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des bases de données Azure SQL db. Si nécessaire, vous pouvez également lier des tables d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès à des tables ou à des tables Azure SQL db.  
  
Pour plus d’informations sur ces tâches et leur exécution, consultez les rubriques suivantes :  
  
-   [Préparation des bases de données Access pour la migration](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Liaison des applications Access à SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
Les sections suivantes décrivent les fonctionnalités de l’interface utilisateur SSMA.  
  
### <a name="metadata-explorers"></a>Explorateurs de métadonnées  
SSMA contient deux explorateurs de métadonnées que vous pouvez utiliser pour parcourir et effectuer des actions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur les bases de données Access et Azure SQL db.  
  
#### <a name="access-metadata-explorer"></a>Accéder à l'explorateur de métadonnées  
L’Explorateur de métadonnées Access affiche des informations sur les bases de données Access qui ont été ajoutées au projet. Lorsque vous ajoutez une base de données Access, SSMA récupère les métadonnées de cette base de données, qui sont les métadonnées qui sont disponibles dans l’Explorateur de métadonnées Access.  
  
Vous pouvez utiliser l’Explorateur de métadonnées Access pour effectuer les tâches suivantes :  
  
-   Parcourez les tables de chaque base de données Access.  
  
-   Sélectionnez les objets à convertir et convertissez les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets en syntaxe. Pour plus d’informations, consultez [conversion d’objets de base de données Access](converting-access-database-objects-accesstosql.md).  
  
-   Sélectionnez des objets pour la migration des données et migrez les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de ces objets vers. Pour plus d’informations, consultez [migration de données Access vers SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Liez et dissociez l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès et les tables.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server ou l’Explorateur de métadonnées Azure SQL DB  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou l’Explorateur de métadonnées de base de données SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche des informations sur une instance de ou Azure SQL db. Lorsque vous vous connectez à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de ou à Azure SQL dB, SSMA récupère les métadonnées relatives à cette instance et les stocke dans le fichier projet.  
  
Vous pouvez utiliser la SQL Server ou l’Explorateur de métadonnées Azure SQL DB pour sélectionner les objets de base de données Access convertis et charger (synchroniser) ces objets dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans Azure SQL db.  
  
Pour plus d’informations, consultez [chargement d’objets de base de données convertis dans SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Métadonnées  
À droite de chaque Explorateur de métadonnées se trouvent des onglets qui décrivent l’objet sélectionné. Par exemple, si vous sélectionnez une table dans l’Explorateur de métadonnées Access, quatre onglets s’affichent : **table**, **mappage de type**, **Propriétés**et **données**. Si vous sélectionnez une table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Explorateur de métadonnées, trois onglets s’affichent : **table**, **SQL**et **données**.  
  
La plupart des paramètres de métadonnées sont en lecture seule. Toutefois, vous pouvez modifier les métadonnées suivantes :  
  
-   Dans l’Explorateur de métadonnées Access, vous pouvez modifier les mappages de types. Veillez à effectuer ces modifications avant de créer des rapports ou de convertir des schémas.  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Explorateur de métadonnées, vous pouvez modifier les propriétés des tables et des index sous l’onglet **table** . Effectuez ces modifications avant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de charger les schémas dans. Pour plus d’informations, consultez [conversion d’objets de base de données Access](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Barres d'outils  
SSMA comporte deux barres d’outils : une barre d’outils de projet et une barre d’outils de migration.  
  
#### <a name="the-project-toolbar"></a>Barre d’outils du projet  
La barre d’outils projet contient des boutons permettant d’utiliser des projets, d’ajouter des fichiers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données Access et de se connecter à ou à Azure SQL db. Ces boutons sont semblables aux commandes du menu **fichier** .  
  
#### <a name="the-migration-toolbar"></a>Barre d’outils de migration  
La barre d’outils de migration contient les commandes suivantes :  
  
|Bouton|Fonction|  
|----------|------------|  
|**Convertir, charger et migrer**|Convertit les bases de données Access, charge les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets convertis dans ou Azure SQL DB et migre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les données vers ou Azure SQL dB, en une seule étape.|  
|**Créer un rapport**|Convertit le schéma d’accès [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionné vers ou la syntaxe Azure SQL dB, puis crée un rapport qui indique la réussite de la conversion.<br /><br />Cette commande est disponible uniquement lorsque des objets sont sélectionnés dans l’Explorateur de métadonnées Access.|  
|**Convertir le schéma**|Convertit le schéma d’accès [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionné en schémas de base de donnée SQL ou Azure.<br /><br />Cette commande est disponible uniquement lorsque des objets sont sélectionnés dans l’Explorateur de métadonnées Access.|  
|**Migrer des données**|Migre les données de la base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données Access vers ou Azure SQL db. Avant d’exécuter cette commande, vous devez convertir les schémas d’accès dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas Azure SQL dB, puis charger les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL db.<br /><br />Cette commande est disponible uniquement lorsque des objets sont sélectionnés dans l’Explorateur de métadonnées Access.|  
|**Stop**|Arrête le processus en cours, par exemple la conversion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’objets vers ou la syntaxe Azure SQL db.|  
  
### <a name="menus"></a>Menus  
SSMA contient les menus suivants :  
  
|Menu|Description|  
|--------|---------------|  
|**File**|Contient des commandes pour l’Assistant Migration, l’utilisation de projets, l’ajout et la suppression de fichiers de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données Access, et la connexion à ou à Azure SQL db.|  
|**Modifier**|Contient des commandes pour rechercher et utiliser du texte dans les pages de détails, telles [!INCLUDE[tsql](../../includes/tsql-md.md)] que la copie à partir du volet d’informations SQL. Pour ouvrir la boîte de dialogue **gérer les signets** , dans le menu modifier, cliquez sur gérer les signets. Dans la boîte de dialogue, vous verrez une liste de signets existants. Vous pouvez utiliser les boutons sur le côté droit de la boîte de dialogue pour gérer les signets.|  
|**Affichage**|Contient la commande **synchroniser les explorateurs de métadonnées** . Cela synchronise les objets entre l’Explorateur de métadonnées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’accès et l’Explorateur de métadonnées Azure SQL db. Contient également des commandes permettant d’afficher et de masquer les volets **sortie** et **liste d’erreurs** , ainsi que les **mises en page** d’options à gérer avec les dispositions.|  
|**outils**|Contient des commandes permettant de créer des rapports, d’exporter des données, de migrer des objets et des données, de lier des tables et d’accéder aux boîtes de dialogue des paramètres globaux et des projets.|  
|**Aide**|Fournit l’accès à l’aide de SSMA et à la boîte de dialogue **à propos** de.|  
  
### <a name="output-pane-and-error-list-pane"></a>Volet de sortie et volet de Liste d’erreurs  
Le menu **affichage** fournit des commandes pour activer/désactiver la visibilité du volet de sortie et du volet de liste d’erreurs :  
  
-   Le volet sortie affiche les messages d’état de SSMA lors de la conversion d’objets, de la synchronisation d’objets et de la migration des données.  
  
-   Le volet Liste d’erreurs affiche les messages d’erreur, d’avertissement et d’information dans une liste que vous pouvez trier.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
