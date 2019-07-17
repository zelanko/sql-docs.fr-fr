---
title: Bien démarrer avec SSMA pour Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: ef71a9355bc11c4d377f00a44b2b8cd2958f8656
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264446"
---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>Bien démarrer avec SSMA pour Oracle (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour Oracle vous permet de rapidement convertir des schémas de base de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schémas, charger les schémas qui en résulte dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migrer les données d’Oracle vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Cette rubrique présente le processus d’installation et permet de vous familiariser avec l’interface utilisateur SSMA.  
  
## <a name="installing-ssma"></a>Installation de SSMA  
Pour utiliser SSMA, vous devez d’abord installer le programme du client SSMA sur un ordinateur pouvant accéder à la base de données Oracle source et l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous devez ensuite installer un pack d’extension et au moins un des fournisseurs Oracle (OLE DB ou [!INCLUDE[vstecado](../../includes/vstecado_md.md)]) sur l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces composants prennent en charge la migration des données et l’émulation des fonctions du système Oracle. Pour obtenir des instructions d’installation, consultez [l’installation de SSMA pour Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md).  
  
Pour démarrer SSMA, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant pour Oracle**, puis cliquez sur  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant pour Oracle**.  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA pour Interface d’utilisateur Oracle  
Une fois SSMA est installé, vous pouvez utiliser SSMA pour migrer des bases de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela permet de vous familiariser avec l’interface utilisateur SSMA avant de commencer. Le diagramme suivant illustre l’interface utilisateur de SSMA, y compris les explorateurs de métadonnées, métadonnées, barres d’outils, sortie et volet Liste d’erreur :  
  
![SSMA pour Oracle, l’interface utilisateur](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA pour Oracle, l’interface utilisateur")  
  
Pour démarrer une migration, vous devez d’abord créer un nouveau projet. Ensuite, vous vous connectez à une base de données Oracle. Après une connexion réussie, les schémas Oracle seront affiche dans l’Explorateur de métadonnées d’Oracle. Vous pouvez ensuite les objets avec le bouton droit dans l’Explorateur de métadonnées d’Oracle pour effectuer des tâches telles que créent des rapports qui évaluent les conversions vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez également effectuer ces tâches en utilisant les menus et barres d’outils.  
  
Vous devez également vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Après une connexion réussie, une hiérarchie de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données apparaissent dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées. Après la conversion de schémas Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schémas, sélectionnez ces schémas convertis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, puis synchronisez les schémas avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Une fois que vous synchronisez des schémas convertis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez revenir à l’Explorateur de métadonnées d’Oracle et migrer des données à partir de schémas Oracle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données.  
  
Pour plus d’informations sur ces tâches et comment les exécuter, consultez [migration de bases de données Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md).  
  
Les sections suivantes décrivent les fonctionnalités de l’interface utilisateur SSMA.  
  
### <a name="metadata-explorers"></a>Explorateurs de métadonnées  
SSMA contient deux explorateurs de métadonnées pour rechercher et effectuer des actions sur Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données.  
  
#### <a name="oracle-metadata-explorer"></a>Explorateur de métadonnées d’Oracle  
Explorateur de métadonnées d’Oracle affiche des informations sur les schémas d’Oracle. En utilisant l’Explorateur de métadonnées d’Oracle, vous pouvez effectuer les tâches suivantes :  
  
-   Parcourir les objets dans chaque schéma.  
  
-   Sélectionner des objets pour la conversion et puis de convertir les objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe. Pour plus d’informations, consultez [conversion des schémas Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
-   Sélectionner des tables pour la migration de données, puis migrer les données à partir de ces tables à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [migration de données Oracle dans SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>Explorateur de métadonnées SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées affiche des informations sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA récupère les métadonnées relatives à cette instance et le stocke dans le fichier projet.  
  
Vous pouvez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner des objets de base de données Oracle convertis, puis synchroniser ces objets avec l’instance de l’Explorateur de métadonnées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Pour plus d’informations, consultez [le chargement des objets de base de données convertis dans SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
### <a name="metadata"></a>Métadonnées  
À droite de chaque Explorateur de métadonnées des onglets qui décrivent l’objet sélectionné. Par exemple, si vous sélectionnez une table dans l’Explorateur de métadonnées d’Oracle, six onglets s’affichent : **Table**, **SQL**, **mappage, le rapport de Type**, **propriétés**, et **données**. Le **rapport** onglet contient des informations uniquement après avoir créé un rapport qui contient l’objet sélectionné. Si vous sélectionnez une table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, les trois onglets s’afficheront : **Table**, **SQL**, et **données**.  
  
La plupart des paramètres de métadonnées sont en lecture seule. Toutefois, vous pouvez modifier les métadonnées suivantes :  
  
-   Dans l’Explorateur de métadonnées d’Oracle, vous pouvez modifier les procédures et mappages de type. Pour convertir les procédures modifiées et mappages de type, apporter des modifications avant de convertir des schémas.  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, vous pouvez modifier le [!INCLUDE[tsql](../../includes/tsql-md.md)] pour les procédures stockées. Pour voir ces modifications dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], apporter ces modifications avant de charger les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Modifications apportées dans l’Explorateur de métadonnées sont répercutées dans les métadonnées du projet, pas dans les bases de données source ou cible.  
  
### <a name="toolbars"></a>Barres d'outils  
SSMA a deux barres d’outils : une barre d’outils du projet et une barre d’outils de migration.  
  
#### <a name="the-project-toolbar"></a>La barre d’outils du projet  
La barre d’outils du projet contient des boutons pour l’utilisation de projets, la connexion à Oracle et la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces boutons se présenter comme les commandes sur le **fichier** menu.  
  
#### <a name="migration-toolbar"></a>Barre d’outils de migration  
Le tableau suivant présente la migration des commandes de barre d’outils :  
  
|Bouton|Fonction|  
|------|--------|  
|**Créer des rapports**|Convertit les objets sélectionnés de Oracle vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, puis crée un rapport qui indique le succès de la conversion a.<br /><br />Cette commande est désactivée, sauf si les objets sont sélectionnés dans l’Explorateur de métadonnées d’Oracle.|  
|**Convertir le schéma**|Convertit les objets sélectionnés de Oracle vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets.<br /><br />Cette commande est désactivée, sauf si les objets sont sélectionnés dans l’Explorateur de métadonnées d’Oracle.|  
|**Migrer des données**|Migre les données à partir de la base de données Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Avant d’exécuter cette commande, vous devez convertir les schémas Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schémas, puis charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Cette commande est désactivée, sauf si les objets sont sélectionnés dans l’Explorateur de métadonnées d’Oracle.|  
|**Arrêter**|Arrête le processus en cours.|  
  
### <a name="menus"></a>Menus  
Le tableau suivant présente les menus SSMA.  
  
|Menu|Description|  
|----|-----------|  
|**File**|Contient des commandes pour travailler avec des projets, la connexion à Oracle et la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Edition**|Contient des commandes pour la recherche et de travailler avec du texte dans les pages de détails, telles que la copie [!INCLUDE[tsql](../../includes/tsql-md.md)] depuis le volet de détails SQL. Contient également le **gérer les signets** option, où vous serez en mesure de voir une liste de signets existants. Vous pouvez utiliser les boutons sur le côté droit de la boîte de dialogue pour gérer les signets.|  
|**Affichage**|Contient le **synchroniser les explorateurs de métadonnées** commande. Qui synchronise les objets entre l’Explorateur de métadonnées d’Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées. Contient également des commandes pour afficher et masquer le **sortie** et **liste d’erreurs** volets et une option **dispositions** pour gérer les dispositions.|  
|**Outils**|Contient des commandes pour créer des rapports et de migrer des objets et données. Permet également d’accéder à la **paramètres globaux** et **paramètres du projet** boîtes de dialogue.|  
|**Testeur**|Contient des commandes pour créer et utiliser des cas de test, référentiel et système de gestion des sauvegardes.|  
|**Aide**|Fournit l’accès à l’aide de SSMA et en le **sur** boîte de dialogue.|  
  
### <a name="output-pane-and-error-list-pane"></a>Volets de sortie et erreur liste  
Le **vue** menu fournit des commandes pour activer/désactiver la visibilité du volet sortie et le volet de la liste d’erreurs :  
  
-   Le volet de sortie affiche les messages d’état à partir de SSMA pendant la conversion des objets, la synchronisation de l’objet et la migration des données.  
  
-   Le volet de liste d’erreurs affiche les messages d’erreur, avertissement et d’information dans une liste pouvant être triée.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de données Oracle dans SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[Référence de l’Interface utilisateur &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
