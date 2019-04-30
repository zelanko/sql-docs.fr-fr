---
title: DLL de configuration de traducteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20453b792ed00b388977fefe3064fd8dfca86147
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63273291"
---
# <a name="translator-setup-dlls"></a>DLL de configuration de convertisseur
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation de traducteur DLL contient le **ConfigTranslator** (fonction), qui retourne l’option par défaut pour un traducteur. Si nécessaire, il invite l’utilisateur pour obtenir ces informations. Pour obtenir une description complète de cette fonction, consultez [référence le programme d’installation de l’API DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Le programme d’installation de traducteur DLL est écrite par le développeur du traducteur. Il peut faire partie du traducteur DLL ou une DLL distincte.
