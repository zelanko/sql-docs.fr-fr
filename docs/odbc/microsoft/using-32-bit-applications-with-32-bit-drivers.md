---
title: Utilisation d’applications 32 bits avec des pilotes 32 bits | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307600"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 32 bits avec des pilotes 32 bits
Vous pouvez exécuter des applications 32 bits avec des pilotes 32 bits. Les applications 32 bits et les pilotes 32 bits utilisent l’API de® Win32.  
  
## <a name="architecture"></a>Architecture  
 L’illustration suivante montre comment les applications 32 bits communiquent avec les pilotes 32 bits. L’application appelle le gestionnaire de pilotes 32 bits, qui à son tour appelle les pilotes 32 bits.  
  
 ![Comment 32&#45;les applications bits communiquent avec les pilotes 32&#45;bits](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  N’utilisez pas la DLL du programme d’installation du thunking 32 bits sur WindowsNT/Windows2000. Bien qu’il porte le même nom de fichier que la DLL du programme d’installation 32 bits, il s’agit d’une DLL différente.  
  
## <a name="administration"></a>Administration  
 Vous pouvez gérer les sources de données des pilotes 32 bits à l’aide de l’administrateur de la source de données ODBC. Pour ouvrir l’administrateur ODBC sur des ordinateurs exécutant Windows 2000, ouvrez le panneau de configuration Windows, double-cliquez sur **Outils d’administration**, puis sur **sources de données (ODBC)**. Sur les ordinateurs exécutant des versions antérieures de Microsoft Windows, l’icône s’intitule **odbc 32 bits** ou simplement **ODBC**.  
  
## <a name="components"></a>Components  
 Le composant ODBC comprend les fichiers suivants pour l’exécution d’applications 32 bits avec des pilotes 32 bits. Ces composants se trouvent dans le répertoire \Redist  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Odbc32. dll|Gestionnaire de pilotes 32 bits|  
|Odbccp32. dll|DLL du programme d’installation de 32 bits|  
|Odbcad32. exe|programme Administrateur ODBC 32 bits|  
|Odbcinst. hlp|Fichier d’aide du programme d’installation|  
|Msvcrt40. dll|Bibliothèque Runtime C|
