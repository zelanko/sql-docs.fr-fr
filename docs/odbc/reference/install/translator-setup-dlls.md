---
description: DLL de configuration de convertisseur
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fe4d514f098773024392666d8f528592d362da4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487392"
---
# <a name="translator-setup-dlls"></a>DLL de configuration de convertisseur
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 La DLL d’installation du traducteur contient la fonction **ConfigTranslator** , qui retourne l’option par défaut pour un traducteur. Si nécessaire, l’utilisateur est invité à entrer ces informations. Pour obtenir une description complète de cette fonction, consultez Référence de l' [API dll du programme d’installation](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 La DLL d’installation du traducteur est écrite par le développeur du traducteur. Il peut faire partie de la DLL du traducteur ou d’une DLL distincte.
