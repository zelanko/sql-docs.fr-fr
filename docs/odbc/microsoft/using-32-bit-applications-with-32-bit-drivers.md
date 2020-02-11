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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b4d14cc65b31a0641149ace931efe46c914ad1b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088166"
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
