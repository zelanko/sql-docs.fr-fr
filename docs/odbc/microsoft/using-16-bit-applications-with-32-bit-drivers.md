---
title: À l’aide d’Applications 16 bits avec les pilotes 32 bits | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: 68feb3b7-c01a-4f42-8df9-f9c182d89325
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ebd6f25758f73e75fd96abb734bc7b0347d5ee0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63209963"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 16 bits avec des pilotes 32 bits
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez le Gestionnaire de pilotes 32 bits ou 64 bits à la place.  
  
 Vous pouvez exécuter des applications 16 bits avec les pilotes 32 bits sur votre système Windows, que le pilote 32 bits n’appelle pas explicitement les fonctions API Win32 qui créent des threads. Le Windows sur le sous-système de Windows (WOW) exécute les applications en mode 16 bits et résout les appels de 16 bits pour le système d’exploitation. ODBC thunking DLL résoudre les appels de 16 bits à partir de l’application pour les pilotes 32 bits. Les applications 16 bits utilisent l’API Windows et les pilotes 32 bits utilisent l’API Win32.  
  
## <a name="architecture"></a>Architecture  
 L’illustration suivante montre comment aux applications 16 bits communiquent avec les pilotes de 32 bits. Entre le Gestionnaire de pilotes 16 bits et les pilotes 32 bits sont génériques thunking DLL qui convertissent des appels ODBC 16 bits en appels ODBC 32 bits.  
  
 ![Comment 16&#45;applications de bits communiquent avec les 32&#45;bit pilotes](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  Chaque fois qu’une application 16 bits interagit avec un pilote 32 bits, le Gestionnaire de pilotes 32 bits retourne toujours « 2.0 » en tant que version d’ODBC pris en charge par le pilote.  
  
## <a name="administration"></a>Administration  
 Vous pouvez gérer les sources de données pour les pilotes 32 bits à l’aide de l’administrateur de sources de données ODBC. Pour ouvrir l’administrateur ODBC sur les ordinateurs exécutant Microsoft® Windows® 2000, ouvrez le panneau de configuration Windows, double-cliquez sur **outils d’administration**, puis double-cliquez sur **Sources de données (ODBC)**. Sur les ordinateurs exécutant des versions antérieures de Microsoft Windows, l’icône est nommée **ODBC 32 bits** ou simplement **ODBC**.  
  
 L’illustration suivante montre comment une application 16 bits appelle une DLL d’installation du pilote 32 bits. Entre le programme d’installation 16 bits DLL et le pilote 32 bits DLL d’installation est une DLL thunking générique qui convertit les appels DLL de programme d’installation 16 bits aux appels DLL de programme d’installation 32 bits.  
  
 ![Comment un 16&#45;bit application appelle un 32&#45;bits des DLL d’installation du pilote](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 Dans Windows sur Windows (thunking de 16 bits vers 32 bits), une DLL thunking supplémentaire nommée convertit Ds32gt.dll valeurs d’argument de 16 bits passées via une installation 32 bits DLL en retour à 16 bits.  
  
## <a name="components"></a>Composants  
 Le composant ODBC du SDK MDAC 2.8 SP1 inclut les fichiers suivants pour l’exécution des applications 16 bits avec les pilotes 32 bits. Ces composants sont dans le répertoire \Redist.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc16gt.dll|16 bits générique thunking DLL ODBC|  
|Odbc32gt.dll|32 bits générique thunking DLL ODBC|  
|Odbccp32.dll|DLL d’installation 32 bits|  
|Odbcad32.exe|programme administrateur de 32 bits|  
|Odbcinst.hlp|Fichier d’aide du programme d’installation|  
|Ds16gt.dll|programme d’installation 16 bits pilote générique thunking DLL|  
|Ctl3d32.dll|bibliothèque de style de fenêtre à trois dimensions de 32 bits|  
  
 En outre, les fichiers suivants, ainsi que le Gestionnaire de pilote de 2.10 ODBC 16 bits, qui ne font pas partie d’ODBC 3.51, sont requis par et doivent être installés avec l’application 16 bits.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc.dll|Gestionnaire de pilotes 16 bits|  
|Odbcinst.dll|DLL d’installation 16 bits|  
|Odbcadm.exe|programme de l’administrateur ODBC 16 bits|
