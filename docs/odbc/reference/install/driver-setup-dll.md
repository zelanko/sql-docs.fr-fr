---
description: DLL de configuration de pilote
title: DLL d’installation du pilote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 79fff6ce68e7860b444ebefa736cb959cd54576b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476205"
---
# <a name="driver-setup-dll"></a>DLL de configuration de pilote
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 La DLL d’installation du pilote contient les fonctions **ConfigDriver** et **ConfigDSN** . **ConfigDriver** effectue des tâches d’installation spécifiques au pilote, telles que la saisie d’informations spécifiques au pilote dans le registre. **ConfigDSN** conserve les informations spécifiques au pilote sur les sources de données dans le registre. Pour obtenir une description complète de ces fonctions, consultez Référence de l' [API dll du programme d’installation](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** appelle les fonctions suivantes dans la dll du programme d’installation pour conserver les informations de la source de données dans le registre :  
  
-   **SQLWriteDSNToIni**. Ajoutez une source de données.  
  
-   **SQLRemoveDSNFromIni**. Supprimer une source de données.  
  
-   **SQLWritePrivateProfileString**. Écrire une valeur spécifique au pilote sous une sous-clé de spécification de source de données.  
  
-   **SQLGetPrivateProfileString**. Lire une valeur spécifique au pilote à partir d’une sous-clé de spécification de source de données.  
  
-   **SQLGetTranslator**. Demander à l’utilisateur un nom et une option de traducteur. Cette fonction appelle **ConfigTranslator** dans la dll d’installation du traducteur.  
  
 La DLL d’installation du pilote est écrite par le développeur du pilote. Il peut faire partie de la DLL du pilote ou d’une DLL distincte.
