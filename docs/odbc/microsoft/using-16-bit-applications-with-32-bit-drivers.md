---
title: Utilisation d’applications 16 bits avec des pilotes 32 bits | Microsoft Docs
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
ms.openlocfilehash: d4be5d2cacaeca7cf53caa330a126284370ec80f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088193"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 16 bits avec des pilotes 32 bits
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez le gestionnaire de pilotes 32 bits ou 64 bits à la place.  
  
 Vous pouvez exécuter des applications 16 bits avec des pilotes 32 bits sur votre système Windows, à condition que le pilote 32 bits n’appelle pas explicitement les fonctions API Win32 qui créent des threads. Le sous-système Windows on Windows (WOW) exécute les applications en mode 16 bits et résout les appels 16 bits au système d’exploitation. Les dll de conversion de thunk ODBC résolvent les appels 16 bits de l’application aux pilotes 32 bits. Les applications 16 bits utilisent l’API Windows et les pilotes 32 bits utilisent l’API Win32.  
  
## <a name="architecture"></a>Architecture  
 L’illustration suivante montre comment les applications 16 bits communiquent avec les pilotes 32 bits. Entre le gestionnaire de pilotes 16 bits et les pilotes 32 bits, il s’agit de dll de thunking génériques qui convertissent des appels ODBC 16 bits en appels ODBC 32 bits.  
  
 ![Comment les 16 applications&#45;bits communiquent avec les pilotes 32&#45;bits](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  Chaque fois qu’une application 16 bits interagit avec un pilote 32 bits, le gestionnaire de pilotes 32 bits retourne toujours « 2,0 » comme version de ODBC prise en charge par le pilote.  
  
## <a name="administration"></a>Administration  
 Vous pouvez gérer les sources de données des pilotes 32 bits à l’aide de l’administrateur de la source de données ODBC. Pour ouvrir l’administrateur ODBC sur des ordinateurs exécutant Microsoft® Windows® 2000, ouvrez le panneau de configuration Windows, double-cliquez sur **Outils d’administration**, puis sur **sources de données (ODBC)**. Sur les ordinateurs exécutant des versions antérieures de Microsoft Windows, l’icône s’intitule **odbc 32 bits** ou simplement **ODBC**.  
  
 L’illustration suivante montre comment une application 16 bits appelle une DLL de configuration de pilote 32 bits. Entre la DLL du programme d’installation 16 bits et la DLL d’installation du pilote 32 bits est une DLL de conversion de pilote générique qui convertit les appels de DLL du programme d’installation 16 bits en appels DLL du programme d’installation de 32 bits.  
  
 ![Comment une application 16&#45;bits appelle une DLL de configuration de pilote 32&#45;bits](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 Dans Windows sur Windows (thunking 16 bits à 32 bits), une DLL de thunking supplémentaire nommée Ds32gt. dll convertit les valeurs d’argument de 16 bits transmises par le biais d’une DLL d’installation 32 bits en 16 bits.  
  
## <a name="components"></a>Components  
 Le composant ODBC du kit de développement logiciel (SDK) MDAC 2,8 SP1 comprend les fichiers suivants pour l’exécution d’applications 16 bits avec des pilotes 32 bits. Ces composants se trouvent dans le répertoire \Redist  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc16gt. dll|DLL de conversion de thunk générique ODBC 16 bits|  
|Odbc32gt. dll|DLL de thunk générique ODBC 32 bits|  
|Odbccp32. dll|DLL du programme d’installation de 32 bits|  
|Odbcad32. exe|programme Administrateur 32 bits|  
|Odbcinst. hlp|Fichier d’aide du programme d’installation|  
|Ds16gt. dll|DLL générique de configuration du pilote 16 bits|  
|Ctl3d32. dll|bibliothèque de styles de fenêtre 3D 32 bits|  
  
 En outre, les fichiers suivants, ainsi que le gestionnaire de pilotes ODBC 2,10 16 bits, qui ne font pas partie d’ODBC 3,51, sont requis par et doivent être installés avec l’application 16 bits.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|ODBC. dll|Gestionnaire de pilotes 16 bits|  
|Odbcinst. dll|DLL du programme d’installation 16 bits|  
|Odbcadm. exe|programme Administrateur ODBC 16 bits|
