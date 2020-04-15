---
title: DLL installation de traducteurs (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28c354fddb36b9e035361fa4ba03fbde34b7d399
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296049"
---
# <a name="translator-setup-dlls"></a>DLL de configuration de convertisseur
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 La configuration du traducteur DLL contient la fonction **ConfigTranslator,** qui renvoie l’option par défaut pour un traducteur. Si nécessaire, il invite l’utilisateur pour ces informations. Pour une description complète de cette fonction, voir [Setup DLL API Reference](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 La configuration du traducteur DLL est écrite par le développeur de traducteurs. Il peut faire partie du traducteur DLL ou d’un DLL séparé.
