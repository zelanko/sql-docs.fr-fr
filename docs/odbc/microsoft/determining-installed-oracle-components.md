---
title: "Détermination installé des composants Oracle | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ODBC driver for Oracle [ODBC], determining installed components
ms.assetid: 3b018f6a-9db0-4aa1-8ec4-afc5f76d7cad
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d0dd661910de02f589511a34c5293b5e7dd8174
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="determining-installed-oracle-components"></a>Détermination installé des composants Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Pour déterminer les composants Oracle installés sur votre système (et leurs versions), accédez au répertoire \Orainst sous le répertoire de base d’Oracle. Ouvrez un des fichiers texte suivants : Nt.rgs, Win95.rgs ou Win98.rgs.  
  
 Le format de fichier est semblable au suivant :  
  
```  
0 ntinstall     all    "orainst"  "3.3.1.0.0C"  "Oracle Installer"  
20 w32tcp80     adp80  "tcp80"    "8.0.5.0.0"   "Oracle TCP/IP Pro"  
23 w32nmp80     adp80  "nmp80"    "8.0.5.0.0"   "Oracle Named Pipe"  
26 w32util80    all    "util80"   "8.0.5.0.0"   "Oracle8 Utilities"  
34 w32rsf80     all    "rsf80"    "8.0.5.0.0"   "Required Support"  
47 w32netclt80  net80  "netc80"   "8.0.5.0.0"   "Oracle Net8 Client"  
69 w32plus80    all    "plus80"   "8.0.5.0.0"   "SQL*Plus"  
```  
  
 Les fichiers .rgs incluent également des informations sur l’installation et les descriptions de chaque composant.
