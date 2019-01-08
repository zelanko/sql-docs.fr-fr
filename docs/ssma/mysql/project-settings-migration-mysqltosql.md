---
title: Paramètres (Migration) (MySQLToSQL) du projet | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4a423404a8f5db4e20331c3b187365a889bea48a
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52408246"
---
# <a name="project-settings-migration-mysqltosql"></a>Paramètres du projet (Migration) (MySQLToSQL)
La page de la Migration de la **paramètres du projet** boîte de dialogue contient les paramètres qui personnalisent comment SSMA migre les données de MySQL vers SQL Server.  
  
Le volet de la Migration est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Pour spécifier les paramètres pour tous les projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet dans **Version cible de Migration** liste déroulante de auquel vous souhaitez accéder aux paramètres, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Migration**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Migration**.  
  
## <a name="options"></a>Options  
  
### <a name="bulk-copy"></a>Copie en bloc  
  
|Terme|Définition|  
|--------|--------------|  
|**Taille de lot**|Spécifie le lot taille utilisée pendant la migration des données.<br /><br />**Par défaut en Mode**:  1000<br /><br />**Mode optimiste**:  1000<br /><br />**Mode plein**:  1000|  
|**Contraintes de validation**|Spécifie si SSMA doit vérifier les contraintes lors de l’insertion des données dans des tables SQL Server.<br /><br />**Par défaut en Mode**:  False<br /><br />**Mode optimiste**:  False<br /><br />**Mode plein**:  False|  
|**Exécuter les déclencheurs**|Spécifie si SSMA doit exécuter les déclencheurs d’insertion lorsqu’il ajoute des données dans des tables SQL Server.<br /><br />**Par défaut en Mode**:  False<br /><br />**Mode optimiste**:  False<br /><br />**Mode plein**:  False|  
|**Conserver l'identité**|Spécifie si SSMA conserve les valeurs d’identité MySQL lorsqu’il ajoute des données à SQL Server. La valeur False provoque des valeurs d’identité doit être assignée par la destination.<br /><br />**Par défaut en Mode**:  True<br /><br />**Mode optimiste**:  True<br /><br />**Mode plein**:  True|  
|**Conserver les valeurs NULL**|Spécifie si SSMA conserve les valeurs null dans la source de données lorsqu’il ajoute des données à SQL Server, indépendamment des valeurs par défaut qui sont spécifiés dans SQL Server.<br /><br />**Par défaut en Mode**:  True<br /><br />**Mode optimiste**:  True<br /><br />**Mode plein**:  True|  
|**Verrou de table**|Spécifie si SSMA verrouille les tables lorsqu’il ajoute des données aux tables pendant la migration de données. Obtient un verrou de mise à jour en bloc pour la durée de l’opération de copie en bloc. Si la valeur est False, un verrou est défini au niveau des lignes.<br /><br />**Par défaut en Mode**:  False<br /><br />**Mode optimiste**:  False<br /><br />**Mode plein**:  False|  
  
### <a name="data-modification"></a>Modification de données  
  
|Terme|Définition|  
|--------|--------------|  
|**Migration de Dates non valides**|Spécifie comment migrer des dates non valides avec comme ' 2007-04-23' ou ' 2000-06-31 10:00:00 » dans les formats de DATE et DATETIME.<br /><br />**Par défaut en Mode**:  Définir NULL<br /><br />**Mode optimiste**:  Définir NULL<br /><br />**Mode plein**:  Définir NULL|  
|**Valeurs de temps négatif Migration**|Spécifie comment migrer les valeurs négatives comme «-30:11:00 » dans les colonnes de temps.<br /><br />**Par défaut en Mode**:  Définir NULL<br /><br />**Mode optimiste**:  Définir NULL<br /><br />**Mode plein**:  Définir NULL|  
|**Valeurs d’heure plus de 24 heures de Migration**|Spécifie la manière de migrer les valeurs de temps de plus de « 23 : 59:59 » dans les colonnes de temps.<br /><br />**Par défaut en Mode**:  Définir NULL<br /><br />**Mode optimiste**:  Définir NULL<br /><br />**Mode plein**:  Définir NULL|  
|**Tronquer les valeurs binaires pour tenir dans la colonne**|Si Oui, SSMA tronque les valeurs binaires à partir de MySQL n’entrent pas dans les colonnes de la table SQL et génère le message d’erreur approprié. Si non, la ligne provoque une erreur<br /><br />**Par défaut en Mode**:  Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:  Non|  
|**Tronquer les valeurs de caractère pour tenir dans la colonne**|SSMA tronque les valeurs de caractère à partir de MySQL n’entrent pas dans les colonnes de la table SQL et génère le message d’erreur approprié.<br /><br />**Par défaut en Mode**:  Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:  Non|  
|**Aucune Migration de Dates**|Spécifie comment migrer les dates de zéro comme « 0000-00-00' ou ' 0000-00-00 00:00:00 » dans les colonnes DATE et DATETIME.<br /><br />**Par défaut en Mode**:  Définir NULL<br /><br />**Mode optimiste**:  Définir NULL<br /><br />**Mode plein**:  Définir NULL|  
|**Un zéro dans la Migration de Dates**|Spécifie comment migrer les dates avec zéro parties comme « 2009-01-00' ou ' 2000-00-00 11:00:00 » dans les colonnes DATE et DATETIME.<br /><br />**Par défaut en Mode**:  Définir NULL<br /><br />**Mode optimiste**:  Définir NULL<br /><br />**Mode plein**:  Définir NULL|  
  
### <a name="migration-engine"></a>Moteur de migration  
  
|Terme|Définition|  
|--------|--------------|  
|**Moteur de migration**|Spécifie le moteur de base de données utilisé lors de la Migration de données. Migration des données côté client fait référence au client SSMA récupérer les données de la source et l’insertion en bloc ces données dans SQL Server. Migration des données côté serveur fait référence au moteur de migration de données SSMA (programme de copie en bloc) en cours d’exécution sur la zone de SQL Server en tant que l’Agent SQL tâche récupérer des données à partir de la source et en insérant directement dans SQL Server, ce qui évite un client supplémentaire-saut (meilleures performances).<br /><br />**Par défaut en Mode**:  Moteur de Migration de données côté client<br /><br />**Mode optimiste**:  Moteur de Migration de données côté client<br /><br />**Mode plein**:  Moteur de Migration de données côté client|  
  
> [!IMPORTANT]  
> Lorsque le **moteur de Migration** option est définie sur **moteur de Migration de données côté serveur**, un nouveau projet de définition d’option **moteur de Migration de données côté serveur utiliser 32 bits** s’affiche . Il spécifie si l’utilitaire de programme de copie en bloc (BCP) 32 bits ou 64 bits est utilisé pour migrer des données.  
  
### <a name="misc"></a>Divers  
  
|Terme|Définition|  
|--------|--------------|  
|**Options de Migration des données étendues**|Affiche les options de migration de données supplémentaires pour chaque table dans l’onglet Détail distinct.<br /><br />**Par défaut en Mode**:  Masquer<br /><br />**Mode optimiste**:  Masquer<br /><br />**Mode plein**:  Masquer|  
|**En cas d’erreur**|Arrête la migration des données lorsqu’une erreur se produit. Il offre trois options :<br /><br />**Arrêter la migration :** Opération de migration de données s’arrête<br /><br />**Passez à la table suivante :** Arrête la migration des données dans la table actuelle et se poursuit à la suivante<br /><br />**Passez à un lot suivant :** Arrête la migration des données dans le lot actuel et se poursuit à la suivante<br /><br />**Par défaut en Mode**: Continuer le lot suivant<br /><br />**Mode optimiste**: Continuer le lot suivant<br /><br />**Mode plein**: Continuer le lot suivant|  
  
### <a name="parallel-data-migration"></a>Migration de données en parallèle  
  
|Terme|Définition|  
|--------|--------------|  
|**Mode de Migration de données en parallèle**|Spécifie le mode utilisé pour les threads de branchement pour permettre la migration de données en parallèle. En mode Auto, SSMA choisit le nombre de threads (10 par défaut) dupliqué pour migrer les données. En mode personnalisé, utilisateur peut spécifier le nombre de threads dupliqué pour migrer des données (valeur minimale est 1 et la valeur maximale est 100). Actuellement, moteur migration client uniquement des données de côté prend en charge la migration de données en parallèle.<br /><br />**Par défaut en Mode**:  Auto<br /><br />**Mode optimiste**:  Auto<br /><br />**Mode plein**:  Auto|  
  
> [!IMPORTANT]  
> Lorsque le **Mode de Migration de données parallèle** option est définie sur **personnalisé**, un nouveau projet de définition d’option **le nombre de threads** s’affiche. Il spécifie le nombre de threads utilisés pour la migration de données.  
  
### <a name="spatial-data"></a>Données spatiales  
  
|Terme|Définition|  
|--------|--------------|  
|**Gestion des erreurs**|Spécifie comment gérer les erreurs de migration de valeurs de types de données spatiales. Si 'Replace avec des valeurs NULL' est spécifié, toutes les valeurs spatiales et provoquent des erreurs seront remplacés par la valeur NULL. Aucun remplacement n’est effectué dans le cas contraire.<br /><br />**Par défaut en Mode**:  Générer une erreur<br /><br />**Mode optimiste**:  Générer une erreur<br /><br />**Mode plein**:  Générer une erreur|  
|**Validation de la valeur**|Spécifie comment gérer des valeurs spatiales non valides. Si la valeur est « Essayez de rendre valide » est spécifié, une tentative est effectuée pour modifier des valeurs non valides pour les rendre valide.<br /><br />**Par défaut en Mode**: Rendre valide<br /><br />**Mode optimiste**: Ne modifiez pas<br /><br />**Mode plein**: Rendre valide|  
  
