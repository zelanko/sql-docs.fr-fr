---
title: Bien démarrer avec SSMA pour MySQL (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Getting started, MySQL metadata explorer
- Getting started, SQL Server or SQL Azure metadata explorer
- Getting started,Installing and licensing
ms.assetid: 8ebfa061-be6f-4a07-923f-8dc832a82f70
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bbfede87cf23da5e8867d33f4b8bad35b6af9c50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679667"
---
# <a name="getting-started-with-ssma-for-mysql-mysqltosql"></a>Bien démarrer avec SSMA pour MySQL (MySQLToSQL)
SQL Server Migration Assistant (SSMA) pour MySQL vous permet de rapidement convertir des schémas de base de données MySQL en schémas SQL Server ou de la base de données SQL Azure, télécharger les schémas qui en résulte dans SQL Server ou Azure SQL DB et migrer des données de MySQL vers SQL Server ou de la base de données SQL Azure.  
  
Cette rubrique présente le processus d’installation et permet de vous familiariser avec l’interface utilisateur SSMA.  
  
## <a name="installing-ssma"></a>Installation de SSMA  
Pour utiliser SSMA, vous devez tout d’abord installer le programme du client SSMA sur un ordinateur pouvant accéder à la base de données MySQL source et l’instance cible de SQL Server ou de la base de données SQL Azure. Ensuite, installez les fournisseurs de MySQL (pilote ODBC MySQL 5.1 (approuvé)) sur l’ordinateur qui exécute le programme du Client SSMA. Pour obtenir des instructions d’installation, consultez [l’installation de SSMA pour MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
  
Pour démarrer SSMA, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **SQL Server Migration Assistant pour MySQL**, puis cliquez sur **migration vers SQL Server L’Assistant pour MySQL**.  
  
## <a name="ssma-for-mysql-user-interface"></a>SSMA pour l'interface d'utilisateur MySQL  
Une fois SSMA est installé et une licence, vous pouvez utiliser SSMA pour migrer des bases de données MySQL vers SQL Server ou de la base de données SQL Azure. Cela permet de vous familiariser avec l’interface utilisateur SSMA avant de commencer. Le diagramme suivant illustre l’interface utilisateur de SSMA, y compris les explorateurs de métadonnées, métadonnées, barres d’outils, sortie et volet Liste d’erreur :  
  
![SSMA pour Interface utilisateur graphique de MySql](../../ssma/mysql/media/ssmaformysqlgui.gif "SSMA pour Interface utilisateur graphique de MySql")  
  
Pour démarrer une migration, vous devez :  
  
1.  Créez un projet.  
  
2.  Se connecter à une base de données MySQL.  
  
3.  Après une connexion réussie, les schémas de MySQL seront affiche dans l’Explorateur de métadonnées de MySQL. Les objets avec le bouton droit dans l’Explorateur de métadonnées de MySQL pour effectuer des tâches telles que créent des rapports qui évaluent les conversions dans SQL Server/Azure SQL DB.  
  
Vous pouvez également effectuer ces tâches en utilisant les menus et barres d’outils.  
  
Vous devez également vous connecter à une instance de SQL Server. Après une connexion réussie, une hiérarchie de bases de données SQL Server s’affiche dans l’Explorateur de métadonnées SQL Server. Une fois que vous convertissez des schémas de MySQL en schémas SQL Server, sélectionnez ces schémas convertis dans l’Explorateur de métadonnées SQL Server et ensuite synchroniser les schémas avec SQL Server.  
  
Vous devez vous connecter à Azure SQL DB si vous avez sélectionné la base de données SQL Azure à partir de la migration sur la liste déroulante dans la boîte de dialogue Nouveau projet. Après une connexion réussie, une hiérarchie de bases de données de base de données SQL Azure s’affiche dans l’Explorateur de métadonnées de base de données SQL Azure. Une fois que vous convertissez des schémas de MySQL pour les schémas de base de données SQL Azure, sélectionnez ces schémas convertis dans l’Explorateur de métadonnées de base de données SQL Azure et ensuite synchroniser les schémas avec la base de données SQL Azure.  
  
Une fois que vous synchronisez des schémas convertis avec SQL Server ou de la base de données SQL Azure, vous pouvez revenir à l’Explorateur de métadonnées de MySQL et migrer des données à partir des schémas de MySQL dans les bases de données SQL Server ou de la base de données SQL Azure.  
  
Pour plus d’informations sur ces tâches et comment les exécuter, consultez [migration de bases de données MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md).  
  
Les sections suivantes décrivent les fonctionnalités de l’interface utilisateur SSMA.  
  
### <a name="metadata-explorers"></a>Explorateurs de métadonnées  
SSMA contient deux explorateurs de métadonnées pour rechercher et effectuer des actions sur les bases de données MySQL et SQL Server.  
  
### <a name="mysql-metadata-explorer"></a>Explorateur de métadonnées de MySQL  
Explorateur de métadonnées de MySQL affiche des informations sur les schémas de MySQL. À l’aide de l’Explorateur de métadonnées MySQL, vous pouvez effectuer les tâches suivantes :  
  
-   Parcourir les objets dans chaque schéma.  
  
-   Sélectionner des objets pour la conversion et puis convertir les objets à la syntaxe de SQL Server. Pour plus d’informations, consultez [conversion de bases de données MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
-   Sélectionner des tables pour la migration de données, puis migrez les données de ces tables vers SQL Server. Pour plus d’informations, consultez [migration des données de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server ou l’Explorateur de métadonnées de base de données SQL Azure  
SQL Server ou l’Explorateur de métadonnées de base de données SQL Azure affiche des informations sur une instance de SQL Server ou de la base de données SQL Azure. Lorsque vous vous connectez à une instance de SQL Server ou de la base de données SQL Azure, SSMA récupère les métadonnées relatives à cette instance et la stocke dans le fichier projet.  
  
Vous pouvez utiliser l’Explorateur de métadonnées pour sélectionner des objets de base de données MySQL convertis et ensuite synchroniser ces objets avec l’instance de SQL Server ou de la base de données SQL Azure.  
  
Pour plus d’informations, consultez [synchronisation (MySQL vers SQL Server / Azure SQL DB)](http://msdn.microsoft.com/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
### <a name="metadata"></a>Métadonnées  
À droite de chaque Explorateur de métadonnées des onglets qui décrivent l’objet sélectionné. Par exemple, si vous sélectionnez une table dans l’Explorateur de métadonnées MySQL, neuf onglets apparaissent : **Table**, **SQL**, **le mappage de Type**, **données**,  **Paramètres**, **mappage de jeu de caractères**, **Modes SQL**, **propriétés**, et **rapport**. Le **rapport** onglet contient des informations uniquement après avoir créé un rapport qui contient l’objet sélectionné. Si vous sélectionnez une table dans l’Explorateur de métadonnées SQL Server, trois onglets apparaissent : **Table**, **SQL** et **données**.  
  
La plupart des paramètres de métadonnées sont en lecture seule. Toutefois, vous pouvez modifier les métadonnées suivantes :  
  
-   Dans l’Explorateur de métadonnées de MySQL, vous pouvez modifier les mappages de type, le mappage de jeu de caractères, les Modes SQL. Pour convertir les mappages de type modifié ou de mappage de jeu de caractères ou de Modes SQL, apporter des modifications avant de convertir des schémas.  
  
-   Dans l’Explorateur de métadonnées SQL Server, vous pouvez modifier les propriétés de table et d’index sur l’onglet de Table. Pour afficher ces modifications dans SQL Server, apportez ces modifications avant de charger les schémas dans SQL Server.  
  
Modifications apportées dans l’Explorateur de métadonnées sont répercutées dans les métadonnées du projet, pas dans les bases de données source ou cible.  
  
### <a name="toolbars"></a>Barres d'outils  
SSMA a deux barres d’outils : une barre d’outils du projet et une barre d’outils de migration.  
  
### <a name="the-project-toolbar"></a>La barre d’outils du projet  
La barre d’outils du projet contient des boutons pour l’utilisation de projets, la connexion à MySQL et la connexion à SQL Server ou de la base de données SQL Azure. Ces boutons se présenter comme les commandes sur le **fichier** menu.  
  
### <a name="migration-toolbar"></a>Barre d’outils de migration  
Le tableau suivant présente la migration des commandes de barre d’outils :  
  
|||  
|-|-|  
|**Bouton**|**Fonction**|  
|**Créer des rapports**|Convertit les objets sélectionnés de MySQL pour les objets SQL Server ou de la base de données SQL Azure et crée ensuite un rapport qui indique le succès de la conversion a.<br /><br />Cette commande est désactivée, sauf si les objets sont sélectionnés dans l’Explorateur de métadonnées de MySQL.|  
|**Convertir le schéma**|Convertit les objets sélectionnés de MySQL pour les objets SQL Server ou de la base de données SQL Azure.<br /><br />Cette commande est désactivée, sauf si les objets sont sélectionnés dans l’Explorateur de métadonnées de MySQL.|  
|**Migrer des données**|Migre les données à partir de la base de données MySQL vers SQL Server ou de la base de données SQL Azure. Avant d’exécuter cette commande, vous devez convertir les schémas de MySQL en schémas SQL Server ou de la base de données SQL Azure et puis charger les objets dans SQL Server ou de la base de données SQL Azure.<br /><br />Cette commande est désactivée, sauf si les objets sont sélectionnés dans l’Explorateur de métadonnées de MySQL.|  
|**Arrêter**|Arrête le processus en cours.|  
  
### <a name="menus"></a>Menus  
Le tableau suivant présente les menus SSMA.  
  
|||  
|-|-|  
|**Menu**|**Description**|  
|**Fichier**|Contient des commandes pour l’utilisation de projets, la connexion à MySQL et la connexion à SQL Server ou de la base de données SQL Azure.|  
|**Modifier**|Contient des commandes pour la recherche et de travailler avec du texte dans les pages de détails. Pour ouvrir **gérer les signets** boîte de dialogue, dans le menu Edition cliquez sur Gérer les signets. Dans la boîte de dialogue, vous verrez une liste de signets existants. Vous pouvez utiliser les boutons sur le côté droit de la boîte de dialogue pour gérer les signets.|  
|**Afficher**|Contient le **synchroniser les explorateurs de métadonnées** commande. Qui synchronise les objets entre l’Explorateur de métadonnées de MySQL et SQL Server ou Explorateur de métadonnées de base de données SQL Azure. Contient également des commandes pour afficher et masquer le **sortie** et **liste d’erreurs** volets et une option **dispositions** pour gérer les mises en page.|  
|**Outils**|Contient des commandes pour créer des rapports, convertir le schéma, Actualiser à partir de la base de données, migrer des objets et des données et enregistrer en tant que Script. Permet également d’accéder à la **paramètres globaux, des paramètres de projet par défaut** et **paramètres du projet** boîtes de dialogue.|  
|**Aide**|Fournit l’accès à l’aide de SSMA et en le **sur** boîte de dialogue.|  
  
### <a name="output-pane-and-error-list-pane"></a>Volets de sortie et erreur liste  
Le **vue** menu fournit des commandes pour activer/désactiver la visibilité du volet sortie et le volet de la liste d’erreurs :  
  
-   Le volet de sortie affiche les messages d’état à partir de SSMA pendant la conversion des objets, la synchronisation de l’objet et la migration des données.  
  
-   Le volet de liste d’erreurs affiche les messages d’erreur, avertissement et d’information dans une liste pouvant être triée.  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
[Migration de données MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
