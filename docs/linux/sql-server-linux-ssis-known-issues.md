---
title: Limitations et problèmes connus pour SSIS sur Linux | Microsoft Docs
description: Cet article décrit les limitations et problèmes connus pour SQL Server Integration Services (SSIS) sur les ordinateurs Linux
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
manager: craigg
ms.date: 06/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: fdf6542f64549233dd5d4ef15dc39a53fefa49a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712838"
---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>Limitations et problèmes connus pour SSIS sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit des limitations et problèmes connus pour SQL Server Integration Services (SSIS) sur Linux.

## <a name="general-limitations-and-known-issues"></a>Problèmes connus et limitations générales

Les fonctionnalités suivantes ne sont pas pris en charge dans cette version de SSIS sur Linux :
  - Base de données catalogue de SSIS
  - Exécution de package planifié par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Capture de données modifiées (CDC)
  - Integration Services (SSIS) Scale Out
  - Feature Pack Azure pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour les autres limitations et problèmes connus avec SSIS sur Linux, consultez le [Notes de publication](sql-server-linux-release-notes.md#ssis).

## <a name="components"></a> Composants pris en charge et non pris en charge

Les composants Integration Services suivants sont pris en charge sur Linux. Certains d'entre eux ont des limitations sur la plateforme Linux. Les composants de SSIS qui ne sont pas répertoriés ici ne sont pas pris en charge sous Linux.

## <a name="supported-control-flow-tasks"></a>Prise en charge des tâches de flux de contrôle
- tâche d'insertion en bloc
- tâche de flux de données
- Tâche de profilage des données
- Tâche d’exécution de requêtes SQL
- Tâche Exécuter l'instruction T-SQL
- Tâche d'expression
- Tâche FTP
- Tâche de service Web
- Tâche XML

## <a name="control-flow-tasks-supported-with-limitations"></a>Tâches de flux de contrôle pris en charge avec les limitations

| Tâche | Limitations |
|------------|---|
| Tâche Exécuter processus | Prend uniquement en charge le mode in-process. |
| Tâche de système de fichiers | Le *déplacement directory* et *définir les attributs de fichier* actions ne sont pas prises en charge. |
| tâche de script | Prend uniquement en charge les API .NET Framework standard. |
| tache Envoyer un message | Prend uniquement en charge le mode d’utilisateur anonyme. |
| Tâche de transfert de base de données | Les chemins d'accès UNC ne sont pas pris en charge. |
| | |

## <a name="supported-and-unsupported-maintenance-plan-tasks"></a>Tâches du plan de maintenance prises en charge et non pris en charge

Dans un plan de maintenance de SQL Server, vous pouvez généralement utiliser diverses tâches SSIS.

Les tâches de plan de maintenance suivantes ne sont pas pris en charge sur Linux :
- Notifier l’opérateur
- Exécuter le travail de l’Agent SQL Server

Les tâches de plan de maintenance suivantes sont prises en charge sur Linux :
- Vérifier l’intégrité de la base de données
- Réduire la base de données
- Réorganiser l'index
- Reconstruction d’Index
- Mettre à jour les statistiques
- Nettoyer l’historique
- Sauvegarder la base de données
- Instruction T-SQL

## <a name="supported-control-flow-containers"></a>Prise en charge des conteneurs de flux de contrôle
- conteneur de séquences
- Conteneur de boucles For
- Conteneur de boucles Foreach

## <a name="supported-data-flow-sources-and-destinations"></a>Sources de flux de données pris en charge et des destinations
- Destination et source de fichier brut
- Source XML

## <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>Sources de flux de données et des destinations prises en charge avec les limitations

| Composant | Limitations |
|------------|---|
| ADO.NET source et destination | Prennent uniquement en charge le fournisseur de données SQLClient. |
| Source de fichier plat et de destination | Prend en charge uniquement les chemins de fichiers Windows-style, auquel la règle de mappage de chemin d’accès par défaut est appliquée. Par exemple `D:\home\ssis\travel.csv` devient `/home/ssis/travel.csv`. |
| Source OData | Prend uniquement en charge l’authentification de base. |
| Source et destination ODBC | Prend en charge des pilotes ODBC Unicode de 64 bits sur Linux. Varie selon le Gestionnaire de pilotes UnixODBC sur Linux. |
| OLE DB source et destination | Prennent uniquement en charge SQL Server Native Client 11.0 et le fournisseur Microsoft OLE DB pour SQL Server. |
| | |

## <a name="supported-data-flow-transformations"></a>Prise en charge des transformations du flux de données
- Agrégat
- Audit
- Distributeur de données équilibrées
- Table des caractères
- Fractionnement conditionnel
- Copie de colonnes
- Conversion de données
- Colonne dérivée
- Exportation de colonne
- Regroupement probable
- Recherche floue
- Importation de colonne
- Lookup
- Fusion
- Merge Join
- Multidiffusion
- Tableau croisé dynamique
- Nombre de lignes
- Dimension à variation lente
- Trier
- Recherche de terme
- Union All
- Supprimer le tableau croisé dynamique

## <a name="data-flow-transformations-supported-with-limitations"></a>Transformations du flux de données pris en charge avec les limitations

| Composant | Limitations |
|------------|---|
| transformation de commande OLE DB | Mêmes limitations que la source OLE DB et la destination. |
| composant Script | Prend uniquement en charge les API .NET Framework standard. |
| | |

## <a name="supported-and-unsupported-log-providers"></a>Modules fournisseurs d’informations prises en charge et non pris en charge
Tous les fournisseurs de journal SSIS intégrés sont pris en charge sur Linux, sauf le fournisseur du journal des événements Windows.

Le fournisseur de journaux SQL Server prend en charge uniquement l’authentification SQL ; Il ne prend pas en charge l’authentification Windows.

Les fournisseurs de journaux SSIS pour SQL Server Profiler pour les fichiers texte et pour les fichiers XML enregistrent leur sortie dans un fichier que vous spécifiez. Les considérations suivantes s’appliquent pour le chemin d’accès de fichier :
-   Si vous ne fournissez pas un chemin d’accès, le fournisseur de journaux écrit dans le répertoire actuel de l’hôte. Si l’utilisateur actuel n’est pas autorisé à écrire dans le répertoire actuel de l’hôte, le fournisseur de journaux génère une erreur.
-   Vous ne pouvez pas utiliser une variable d’environnement dans un chemin d’accès de fichier. Si vous spécifiez une variable d’environnement, le texte littéral que vous spécifiez s’affiche dans le chemin d’accès de fichier. Par exemple, si vous spécifiez `%TMP%/log.txt`, le fournisseur de journaux ajoute du texte littéral `/%TMP%/log.txt` vers le répertoire actuel de l’hôte.

## <a name="related-content-about-ssis-on-linux"></a>Contenu associé sur SSIS sur Linux
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Configurer SQL Server Integration Services sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md)
-   [L’exécution sur Linux avec cron du package de planification SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
