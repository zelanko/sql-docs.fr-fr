---
title: Paramétrage d’une base de données à l’aide d’une charge de travail du magasin de requêtes | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor, Query Store
ms.assetid: 17107549-5073-4fa2-8ee7-5ed33b38821e
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 439967d45e74b0069d3064af64393151f9efc735
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376601"
---
# <a name="tuning-database-using-workload-from-query-store"></a>Paramétrage d’une base de données à l’aide d’une charge de travail du magasin de requêtes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]


La fonctionnalité [Magasin des requêtes](../../relational-databases/performance/how-query-store-collects-data.md) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] capture automatiquement un historique des requêtes, des plans et des statistiques d’exécution, et conserve ces informations dans la base de données. L’[Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md) prend en charge une nouvelle option permettant d’utiliser le magasin de requêtes pour sélectionner automatiquement une charge de travail appropriée pour le paramétrage. Pour de nombreux utilisateurs, cela peut supprimer la nécessité de collecter de manière explicite une charge de travail pour le paramétrage. Cette fonctionnalité est disponible uniquement si la fonctionnalité de magasin de requêtes est activée pour la base de données. 
  
Cette fonctionnalité est disponible avec [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **v16.4** ou version ultérieure. 
  
## <a name="how-to-tune-a-workload-from-query-store-in-database-engine-tuning-advisor-gui"></a>Comment paramétrer une charge de travail à partir du magasin de requêtes dans l’interface graphique utilisateur de l’Assistant Paramétrage du moteur de base de données
Dans l’interface graphique utilisateur de l’Assistant Paramétrage du moteur de base de données, sélectionnez la case d’option **Magasin de requêtes** dans le volet **Général** pour activer cette fonctionnalité (voir la figure ci-dessous).

![Charge de travail de l’Assistant Paramétrage du moteur de base de données à partir du Magasin des requêtes](../../relational-databases/performance/media/dta-workload-from-query-store.gif)
 
## <a name="how-to-tune-a-workload-from-query-store-in-dtaexe-command-line-utility"></a>Comment paramétrer une charge de travail à partir du magasin de requête dans l’utilitaire en ligne de commande dta.exe
À partir de la ligne de commande (dta.exe), choisissez l’option  **-iq** pour sélectionner la charge de travail dans le magasin de requêtes. 

Deux options supplémentaires, disponibles par l’intermédiaire de la ligne de commande, vous permettent de paramétrer le comportement de l’Assistant Paramétrage du moteur de base de données lors de la sélection de la charge de travail à partir du magasin de requêtes. Ces options ne sont pas disponibles par l’intermédiaire de l’interface graphique utilisateur :
  1. **Nombre d’événements de charge de travail à paramétrer** : cette option, spécifiée à l’aide de l’argument de ligne de commande  **-n**, permet à l’utilisateur de contrôler le nombre d’événements du magasin des requêtes qui sont paramétrés. Par défaut, l’Assistant Paramétrage du moteur de base de données utilise la valeur 1000 pour cette option. L’Assistant Paramétrage du moteur de base de données choisit toujours les événements les plus coûteux par durée totale. 
  
  2. **Fenêtres temps des événements à paramétrer** : le magasin des requêtes pouvant contenir des requêtes qui ont été exécutées il y a longtemps, cette option permet à l’utilisateur de spécifier une fenêtre de temps écoulé (en heures) avant laquelle une requête doit avoir été exécutée pour être prise en compte par l’Assistant Paramétrage du moteur de base de données pour le paramétrage. Cette option est spécifiée à l’aide de l’argument de ligne de commande  **-je**. 

Pour plus d’informations, consultez [Utilitaire dta](../../tools/dta/dta-utility.md).

## <a name="difference-between-using-workload-from-query-store-and-plan-cache"></a>Différence entre l’utilisation d’une charge de travail du magasin de requêtes et celle du cache du plan 
La différence entre les options Magasin de requêtes et Cache du plan est que la première contient un historique plus long des requêtes qui ont été exécutées sur la base de données, lesquelles sont conservées après les redémarrages successifs du serveur. D’autre part, le cache du plan contient uniquement un sous-ensemble de requêtes exécutées récemment dont les plans sont mis en cache dans la mémoire. Quand le serveur redémarre, les entrées du cache du sont effacées.

## <a name="see-also"></a> Voir aussi  
[Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md)     
[Didacticiel : Assistant Paramétrage du moteur de base de données](Tutorial:%20Database%20Engine%20Tuning%20Advisor.md)     
[Comment le Magasin des requêtes collecte les données](../../relational-databases/performance/how-query-store-collects-data.md)     
[Bonnes pratiques en matière de magasin de requêtes](../../relational-databases/performance/best-practice-with-the-query-store.md)
