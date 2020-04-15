---
title: Exigences matérielles et logicielles (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe69775e379e9a9d661b4ddf81e577b738fcf34d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295239"
---
# <a name="hardware-and-software-requirements-odbc"></a>Configuration matérielle et logicielle requise (ODBC)
Ce sujet répertorie les exigences relatives à l’utilisation des pilotes de base de données de bureau ODBC.  
  
## <a name="hardware-requirements"></a>Configuration matérielle  
 Pour utiliser les pilotes de base de données de bureau ODBC, vous devez avoir :  
  
-   Un ordinateur personnel compatible AVEC IBM.  
  
-   Un disque dur avec 6 Mo d’espace disque libre.  
  
-   Au moins 16 Mo de mémoire d’accès aléatoire (RAM).  
  
## <a name="software-requirements"></a>Configuration logicielle  
 Pour accéder aux données avec un chauffeur ODBC, vous devez avoir :  
  
-   Le conducteur de l’ODBC.  
  
-   Le gestionnaire de pilote ODBC 32 bits, version 3.51 ou plus tard (Odbc32.dll).  
  
-   Microsoft Windows 95 ou plus tard, ou Windows NT 4.0 ou Windows 2000.  
  
-   Une taille de pile d’au moins 20 KB pour une application utilisant un pilote Microsoft ODBC.  
  
 Lorsque vous utilisez Microsoft Windows NT 4.0 ou Windows 2000, le pilote 32 bits est sans fil, mais seulement grâce à l’utilisation d’un sémaphore global qui contrôle l’accès au pilote. L’utilisation simultanée du pilote est très limitée sous Windows NT. Tous les accès à la couche Jet ISAM seront à thread unique pour toutes les applications utilisant le moteur Microsoft Jet.  
  
 Lorsque vous exécutez plusieurs applications 16 bits sur Windows sur Windows sur Windows (WOW) sur Microsoft Windows NT 4.0, les applications doivent être exécutées dans des espaces de mémoire séparés. (Le même espace de mémoire ne peut pas être utilisé parce que ODBC ne prend pas en charge plusieurs environnements dans le même processus.) Pour exécuter une application dans un espace mémoire séparé, sélectionnez l’icône de l’application dans le gestionnaire de programme, ouvrez le menu **De fichier** et cliquez sur **Propriétés,** puis cliquez sur **Run In Separate Memory Space**.  
  
 L’utilisation de ces pilotes par des applications 16 bits sur Windows 95 n’est pas prise en charge.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Besoins matériels et logiciels spécifiques au conducteur  
  
-   Les fichiers MicrosoftAccess et dBASEdrivers peuvent nécessiter des modifications dans les fichiers Autoexec.bat ou Config.sys.
