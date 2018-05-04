---
title: DLL du programme d’installation traducteur | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2aabec831ba9b623a24f261551684e9bb259e24
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="translator-setup-dlls"></a>DLL de programme d’installation de conversion
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation du traducteur DLL contient le **ConfigTranslator** (fonction), qui retourne l’option par défaut pour un traducteur. Si nécessaire, il invite l’utilisateur pour obtenir des informations. Pour obtenir une description complète de cette fonction, consultez [référence le programme d’installation de l’API DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Le programme d’installation du traducteur DLL est écrite par le développeur du traducteur. Il peut faire partie du traducteur DLL ou une DLL distincte.
