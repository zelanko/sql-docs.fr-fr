---
title: Dll d’installation du traducteur | Microsoft Docs
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
ms.openlocfilehash: b6c99dffc94f2675efdbbc3d5c1d142a5ae9b7e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093839"
---
# <a name="translator-setup-dlls"></a>DLL de configuration de convertisseur
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 La DLL d’installation du traducteur contient la fonction **ConfigTranslator** , qui retourne l’option par défaut pour un traducteur. Si nécessaire, l’utilisateur est invité à entrer ces informations. Pour obtenir une description complète de cette fonction, consultez Référence de l' [API dll du programme d’installation](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 La DLL d’installation du traducteur est écrite par le développeur du traducteur. Il peut faire partie de la DLL du traducteur ou d’une DLL distincte.
