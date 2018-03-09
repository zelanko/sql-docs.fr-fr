---
title: "DLL du programme d’installation traducteur | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ce6961ec470bf0e0a7281a129d85f5cf69c9b80
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="translator-setup-dlls"></a>DLL de programme d’installation de conversion
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation du traducteur DLL contient le **ConfigTranslator** (fonction), qui retourne l’option par défaut pour un traducteur. Si nécessaire, il invite l’utilisateur pour obtenir des informations. Pour obtenir une description complète de cette fonction, consultez [référence le programme d’installation de l’API DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Le programme d’installation du traducteur DLL est écrite par le développeur du traducteur. Il peut faire partie du traducteur DLL ou une DLL distincte.
