---
title: "DLL du programme d’installation traducteur | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc2fa42c2535d794dcf93160bf79b71d8c226640
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="translator-setup-dlls"></a>DLL de programme d’installation de conversion
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation du traducteur DLL contient le **ConfigTranslator** (fonction), qui retourne l’option par défaut pour un traducteur. Si nécessaire, il invite l’utilisateur pour obtenir des informations. Pour obtenir une description complète de cette fonction, consultez [référence le programme d’installation de l’API DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Le programme d’installation du traducteur DLL est écrite par le développeur du traducteur. Il peut faire partie du traducteur DLL ou une DLL distincte.

