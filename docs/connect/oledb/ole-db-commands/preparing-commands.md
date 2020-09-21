---
title: Préparation des commandes (pilote OLE DB)
description: Pour une commande unique exécutée plusieurs fois, OLE DB Driver pour SQL Server prend en charge la préparation des commandes pour améliorer les performances.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- prepared statements [OLE DB Driver for SQL Server]
- commands [OLE DB]
- command preparation [OLE DB Driver for SQL Server]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5b2bb5f167361ad5fec4a5580c49378144cbbf26
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862420"
---
# <a name="preparing-commands"></a>Préparation des commandes
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server prend en charge la préparation des commandes pour l’exécution multiple optimisée d’une même commande ; cependant, la préparation des commandes génère une charge mémoire et un consommateur n’a pas besoin de préparer une commande pour l’exécuter plusieurs fois. En général, la préparation de commande est nécessaire si celle-ci doit être exécutée plus de trois fois.  
  
 Pour des raisons de performance, la préparation de commande est différée jusqu'à ce que la commande soit exécutée. Il s'agit du comportement par défaut. Toute erreur dans la commande en cours de préparation est inconnue tant que la commande n'a pas été exécutée ou qu'une opération de métapropriété n'a pas été effectuée. L'affectation de la valeur FALSE à la propriété [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSPROP_DEFERPREPARE peut désactiver ce comportement par défaut.  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], lorsqu'une commande est exécutée directement (sans la préparer au préalable), un plan d'exécution est créé et mis en cache. Si l'instruction SQL est réexécutée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dispose d'un algorithme efficace pour faire correspondre la nouvelle instruction au plan d'exécution existant dans le cache et réutilise le plan d'exécution pour cette instruction.  
  
 Pour les commandes préparées, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit la prise en charge native de la préparation et de l'exécution des instructions de commande. Lorsque vous préparez une instruction, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crée un plan d'exécution, le met en cache et retourne un handle de ce plan d'exécution au fournisseur. Le fournisseur utilise ensuite ce handle pour exécuter l'instruction à plusieurs reprises. Aucune procédure stockée n'est créée. Étant donné que le handle identifie directement le plan d'exécution pour une instruction SQL au lieu de faire correspondre l'instruction au plan d'exécution dans le cache (comme c'est le cas pour l'exécution directe), il est plus efficace de préparer une instruction que de l'exécuter directement, si vous savez que l'instruction sera exécutée plusieurs fois.  
  
 Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], les instructions préparées ne peuvent pas être utilisées pour créer des objets temporaires et elles ne peuvent pas référencer des procédures stockées système qui créent des objets temporaires, comme des tables temporaires. Ces procédures doivent être exécutées directement.  
  
 Certaines commandes ne doivent jamais être préparées. Par exemple, les commandes qui spécifient l'exécution de procédure stockée ou incluent du texte non valide pour la création de procédure stockée [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne doivent pas être préparées.  
  
 Si une procédure stockée temporaire est créée, le pilote OLE DB pour SQL Server exécute la procédure stockée temporaire et retourne des résultats comme si l’instruction elle-même avait été exécutée.  
  
 La création d’une procédure stockée temporaire est contrôlée par la propriété d’initialisation spécifique au pilote OLE DB pour SQL Server SSPROP_INIT_USEPROCFORPREP. Si la valeur de la propriété est SSPROPVAL_USEPROCFORPREP_ON ou SSPROPVAL_USEPROCFORPREP_ON_DROP, le pilote OLE DB pour SQL Server tente de créer une procédure stockée quand une commande est préparée. La création de procédure stockée réussit si l'utilisateur d'application a des autorisations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] suffisantes.  
  
 Pour les consommateurs qui se déconnectent rarement, la création de procédures stockées temporaires peut nécessiter des ressources significatives de **tempdb**, la base de données système de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] où les objets temporaires sont créés. Quand la valeur de SSPROP_INIT_USEPROCFORPREP est SSPROPVAL_USEPROCFORPREP_ ON, les procédures stockées temporaires créées par le pilote OLE DB pour SQL Server sont supprimées seulement quand la session qui a créé la commande perd sa connexion à l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si cette connexion est la connexion par défaut créée lors de l'initialisation de la source de données, la procédure stockée temporaire est supprimée uniquement lorsque la source de données devient non initialisée.  
  
 Quand la valeur de SSPROP_INIT_USEPROCFORPREP est SSPROPVAL_USEPROCFORPREP_ON_DROP, les procédures stockées temporaires du pilote OLE DB pour SQL Server sont supprimées quand une des conditions suivantes est réalisée :  
  
-   Le consommateur utilise **ICommandText::SetCommandText** pour indiquer une nouvelle commande.  
  
-   Le consommateur utilise **ICommandPrepare::Unprepare** pour indiquer qu’il n’a plus besoin du texte de la commande.  
  
-   Le consommateur libère toutes les références à l'objet de commande à l'aide de la procédure stockée temporaire.  
  
 Un objet de commande a au plus une procédure stockée temporaire dans **tempdb**. Toute procédure stockée temporaire existante représente le texte de commande actuel d'un objet de commande spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../oledb/ole-db-commands/commands.md)  
  
  
