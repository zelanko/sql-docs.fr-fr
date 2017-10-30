---
title: "Limitations et problèmes connus pour SSIS sur Linux | Documents Microsoft"
description: "Cet article décrit les limitations et problèmes connus pour SQL Server Integration Services (SSIS) sur les ordinateurs Linux"
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: eec45efe8fb49afefab418130d05d7a2b82bddd3
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>Limitations et problèmes connus pour SSIS sur Linux

Cette rubrique décrit les problèmes connus et les limitations actuelles pour SQL Server Integration Services (SSIS) sur Linux.

## <a name="general-limitations-and-known-issues"></a>Limitations générales et les problèmes connus

Les fonctionnalités suivantes ne sont pas pris en charge dans cette version de SSIS sur Linux :
  - Base de données du catalogue SSIS
  - Exécution du package planifiés par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Capture de données modifiées (CDC)
  - Avec montée en puissance SSIS
  - Azure Feature Pack pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour les autres limitations et problèmes connus avec SSIS sur Linux, consultez le [Notes de publication](sql-server-linux-release-notes.md#ssis).

## <a name="components"></a>Composants pris en charge et non pris en charge

Les composants Integration Services intégrés suivants sont pris en charge sous Linux. Certaines d'entre elles ont des limitations sur la plate-forme Linux, comme décrit dans les tableaux suivants.

Les composants intégrés qui ne sont pas répertoriés ici ne sont pas pris en charge sous Linux.

### <a name="supported-control-flow-tasks"></a>Prise en charge des tâches de flux de contrôle
- tâche d'insertion en bloc
- tâche de flux de données
- Tâche de profilage des données
- Tache d'exécution de requêtes SQL
- Tâche Exécuter l'instruction T-SQL
- Tâche d'expression
- Tâche FTP
- Tâche de service Web
- Tâche XML

### <a name="control-flow-tasks-supported-with-limitations"></a>Tâches de flux de contrôle pris en charge avec les limitations

| Tâche | Limitations |
|------------|---|
| Exécuter la tâche de processus | Prend uniquement en charge le mode in-process. |
| Tâche de système de fichiers | Le *répertoire de déplacement* et *définir les attributs de fichier* actions ne sont pas prises en charge. |
| tâche de script | Prend uniquement en charge les API .NET Framework standard. |
| tache Envoyer un message | Prend en charge uniquement en mode utilisateur anonyme. |
| Tâche de transfert de base de données | Les chemins d'accès UNC ne sont pas pris en charge. |
| | |

### <a name="supported-control-flow-containers"></a>Prise en charge des conteneurs de flux de contrôle
- conteneur de séquences
- Conteneur de boucles For
- Conteneur de boucles Foreach

### <a name="supported-data-flow-sources-and-destinations"></a>Sources de flux de données pris en charge et des destinations
- Destination et source de fichier brut
- Source XML

### <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>Sources de flux de données et des destinations prises en charge avec les limitations

| Composant | Limitations |
|------------|---|
| ADO.NET source et destination | Prennent uniquement en charge le fournisseur de données SQLClient. |
| Source de fichier plat et de destination | Prend en charge uniquement les chemins de fichier Windows de style, auquel la règle de mappage du chemin d’accès par défaut est appliquée. Par exemple `D:\home\ssis\travel.csv` devient `/home/ssis/travel.csv`. |
| Source OData | Prend uniquement en charge l’authentification de base. |
| ODBC source et destination | Prend en charge des pilotes ODBC Unicode de 64 bits sur Linux. Varie selon le Gestionnaire de pilotes UnixODBC sur Linux. |
| OLE DB source et destination | Prennent uniquement en charge SQL Server Native Client 11.0 et le fournisseur Microsoft OLE DB pour SQL Server. |
| | |

### <a name="supported-data-flow-transformations"></a>Prise en charge les transformations du flux de données
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

### <a name="data-flow-transformations-supported-with-limitations"></a>Transformations du flux de données pris en charge avec les limitations

| Composant | Limitations |
|------------|---|
| transformation de commande OLE DB | Mêmes limitations que OLE DB source et de destination. |
| composant Script | Prend uniquement en charge les API .NET Framework standard. |
| | |

### <a name="supported-and-unsupported-log-providers"></a>Modules fournisseurs d’informations de prise en charge et non pris en charge
Tous les modules fournisseurs d’informations SSIS intégrées sont prises en charge sous Linux, sauf le fournisseur du journal des événements Windows.

Le fournisseur de journaux SQL Server prend en charge uniquement l’authentification SQL ; Il ne prend pas en charge l’authentification Windows.

Les fournisseurs de journal SSIS pour SQL Server Profiler pour les fichiers texte et pour les fichiers XML enregistrent leur sortie dans un fichier que vous spécifiez. Les considérations suivantes s’appliquent au chemin de fichier :
-   Si vous ne fournissez pas un chemin d’accès, le fournisseur de journaux est écrit dans le répertoire actuel de l’hôte. Si l’utilisateur actuel n’est pas autorisé à écrire dans le répertoire actuel de l’hôte, le fournisseur de journaux génère une erreur.
-   Vous ne pouvez pas utiliser une variable d’environnement dans un chemin d’accès de fichier. Si vous spécifiez une variable d’environnement, le texte littéral que vous spécifiez s’affiche dans le chemin d’accès de fichier. Par exemple, si vous spécifiez `%TMP%/log.txt`, le fournisseur de journaux ajoute le texte littéral `/%TMP%/log.txt` vers le répertoire actuel de l’hôte.


