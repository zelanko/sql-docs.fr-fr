---
title: Utilisation d’applications 16 bits avec des pilotes 32 bits ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c919ed8c3f3791720d67ebdcbf5cfbdbea2a0455
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307630"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 16 bits avec des pilotes 32 bits
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt un gestionnaire de pilote 32 ou 64 bits.  
  
 Vous pouvez exécuter des applications 16 bits avec des pilotes 32 bits sur votre système Windows tant que le pilote 32 bits n’appelle pas explicitement les fonctions Win32 API qui créent des threads. Le sous-système Windows on Windows (WOW) exécute les applications en mode 16 bits et résout les appels 16 bits vers le système d’exploitation. Les DL de thunking ODBC résolvent les appels 16 bits de l’application aux pilotes 32 bits. Les applications 16 bits utilisent l’API Windows, et les pilotes 32 bits utilisent l’API Win32.  
  
## <a name="architecture"></a>Architecture  
 L’illustration suivante montre comment les applications 16 bits communiquent avec les conducteurs 32 bits. Entre le Driver Manager 16 bits et les pilotes 32 bits sont génériques Thunking DLLs qui convertissent les appels 16 bits ODBC à des appels 32 bits ODBC.  
  
 ![Comment 16&#45;applications bits communiquer avec 32&#45;bits pilotes](../../odbc/microsoft/media/sdka2.gif "sdka2 (en)")  
  
> [!NOTE]  
>  Chaque fois qu’une application 16 bits interagit avec un pilote 32 bits, le Driver Manager 32 bits retourne toujours «2.0» comme la version d’ODBC prise en charge par le conducteur.  
  
## <a name="administration"></a>Administration  
 Vous pouvez gérer les sources de données pour les pilotes 32 bits en utilisant l’administrateur de source de données ODBC. Pour ouvrir l’administrateur ODBC sur les ordinateurs exécutant Microsoft® Windows® 2000, ouvrez le panneau de contrôle Windows, double clic **outils administratifs,** puis double clic **Sources de données (ODBC)**. Sur les ordinateurs exécutant les versions précédentes de Microsoft Windows, l’icône est nommée **32 bits ODBC** ou tout simplement **ODBC**.  
  
 L’illustration suivante montre comment une application 16 bits appelle un DLL de configuration de pilote 32 bits. Entre l’installateur 16 bits DLL et la configuration du pilote 32 bits DLL est un Thunking générique DLL qui convertit 16 bits installateur DLL appels à 32 bits installateur DLL appels.  
  
 ![Comment une application 16&#45;bit appelle un 32&#45;bit configuration pilote DLL](../../odbc/microsoft/media/sdka3.gif "sdka3 (en)")  
  
 Dans Windows on Windows (16 bits à 32 bits thunking), un DLL thunking supplémentaire nommé Ds32gt.dll convertit les valeurs d’argument 16 bits passé par une configuration 32 bitS DLL retour à 16 bits.  
  
## <a name="components"></a>Components  
 La composante ODBC du MDAC 2.8 SP1 SDK comprend les fichiers suivants pour l’exécution d’applications 16 bits avec des pilotes 32 bits. Ces composants sont dans l’annuaire redist.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc16gt.dll|16 bits ODBC générique thunking DLL|  
|Odbc32gt.dll|32 bits ODBC générique thunking DLL|  
|Odbccp32.dll|Installateur 32 bits DLL|  
|Odbcad32.exe|Programme d’administrateur 32 bits|  
|Odbcinst.hlp|Fichier d’aide à l’installateur|  
|Ds16gt.dll|Installation de pilote 16 bits générique thunking DLL|  
|Ctl3d32.dll|Bibliothèque de style fenêtre en trois dimensions 32 bits|  
  
 En outre, les fichiers suivants ainsi que le gestionnaire de pilote 16 bits ODBC 2.10, qui ne font pas partie de ODBC 3.51, sont requis par et doivent être installés avec l’application 16 bits.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc.dll|Gestionnaire de pilote 16 bits|  
|Odbcinst.dll|16 bits Installateur DLL|  
|Odbcadm.exe|Programme d’administrateur ODBC 16 bits|
