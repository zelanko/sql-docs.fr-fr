---
title: Utilisation d’applications 32 bits avec des pilotes 32 bits ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31512f9339b9d46225bb4f1198cb617a48509acb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307600"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 32 bits avec des pilotes 32 bits
Vous pouvez exécuter des applications 32 bits avec des pilotes 32 bits. Les applications 32 bits et les pilotes 32 bits utilisent l’API Win32®.  
  
## <a name="architecture"></a>Architecture  
 L’illustration suivante montre comment les applications 32 bits communiquent avec les conducteurs 32 bits. L’application appelle le Driver Manager 32 bits, qui à son tour appelle les pilotes 32 bits.  
  
 ![Comment 32&#45;applications bits communiquer avec 32&#45;bits pilotes](../../odbc/microsoft/media/sdka6.gif "sdka6 (en)")  
  
> [!IMPORTANT]  
>  N’utilisez pas l’installateur de thunking 32 bits DLL sur WindowsNT/Windows2000. Bien qu’il ait le même nom de fichier que l’installateur 32 bits DLL, il s’agit d’un DLL différent.  
  
## <a name="administration"></a>Administration  
 Vous pouvez gérer les sources de données pour les pilotes 32 bits en utilisant l’administrateur de source de données ODBC. Pour ouvrir l’administrateur ODBC sur les ordinateurs exécutant Windows 2000, ouvrez le panneau de contrôle Windows, double clic **outils administratifs,** puis double clic **Sources de données (ODBC)**. Sur les ordinateurs exécutant les versions précédentes de Microsoft Windows, l’icône est nommée **32 bits ODBC** ou tout simplement **ODBC**.  
  
## <a name="components"></a>Components  
 Le composant ODBC comprend les fichiers suivants pour l’exécution d’applications 32 bits avec des pilotes 32 bits. Ces composants sont dans l’annuaire redist.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc32.dll|Gestionnaire de pilote 32 bits|  
|Odbccp32.dll|32 bits Installateur DLL|  
|Odbcad32.exe|Programme d’administrateur ODBC 32 bits|  
|Odbcinst.hlp|Fichier d’aide à l’installateur|  
|Msvcrt40.dll Msvcrt40.dll Msvcrt40.dll Msvc|C bibliothèque de temps d’exécution|
