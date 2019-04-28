---
title: Cibles des événements étendus SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97dbdfcdbc1ddf2a8aba10845f1bc5e3c785a9ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842514"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server Extended Events Targets
  Les cibles des Événements étendus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont des consommateurs d'événements. Les cibles peuvent écrire dans un fichier, stocker des données d'événement dans une mémoire tampon ou agréger des données d'événement. Les cibles peuvent traiter des données de façon synchrone ou asynchrone.  
  
 La conception des Événements étendus garantit que les cibles sont assurées de recevoir des événements une seule fois par session.  
  
 Les Événements étendus fournissent les cibles suivantes que vous pouvez utiliser pour une session Événements étendus :  
  
-   [Compteur d’événements](../../2014/database-engine/event-counter-target.md)  
  
     Permet de comptabiliser tous les événements qui surviennent au cours d'une session Événements étendus. Permet d'obtenir des informations sur les caractéristiques de charge de travail sans ajouter la surcharge de la collecte d'événements complète. Il s'agit d'une cible synchrone.  
  
-   [Fichier d’événements](../../2014/database-engine/event-file-target.md)  
  
     Permet d'enregistrer sur le disque les résultats d'une session d'événements stockés en mémoire tampon. Il s'agit d'une cible asynchrone.  
  
-   [Appariement d’événements](../../2014/database-engine/event-pairing-target.md)  
  
     De nombreux événements surviennent sous forme de paires, tels que les acquisitions et les libérations de verrous. Permet de savoir si un événement jumelé n'entre pas dans le cadre d'une correspondance. Il s'agit d'une cible asynchrone.  
  
-   [Suivi d’événements pour Windows (ETW)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     Permet de mettre en corrélation les événements [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec les données d’événement du système d’exploitation Windows ou des applications. Il s'agit d'une cible synchrone.  
  
-   [Histogramme](../../2014/database-engine/histogram-target.md)  
  
     À utiliser pour comptabiliser le nombre d'occurrences d'un événement donné, en fonction d'une colonne d'événement ou d'une action définie. Il s'agit d'une cible asynchrone.  
  
-   [Mémoire tampon en anneau](../../2014/database-engine/ring-buffer-target.md)  
  
     Permet de conserver les événements en mémoire selon le principe FIFO (premier entré/premier sorti) ou au cas par cas. Il s'agit d'une cible asynchrone.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../relational-databases/extended-events/extended-events.md)   
 [Packages d’événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [Sessions Événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 [Moteur des événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
