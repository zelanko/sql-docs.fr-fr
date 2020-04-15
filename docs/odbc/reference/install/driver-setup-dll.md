---
title: Installation du pilote DLL (fr) Microsoft Docs
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
ms.openlocfilehash: a0a2878591c92fe0b2070a295d9dc622c245c17e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306420"
---
# <a name="driver-setup-dll"></a>DLL de configuration de pilote
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 La configuration du conducteur DLL contient les fonctions **ConfigDriver** et **ConfigDSN.** **ConfigDriver** effectue des tâches d’installation spécifiques au conducteur, telles que la saisie d’informations spécifiques au conducteur dans le registre. **ConfigDSN** conserve des renseignements spécifiques au conducteur sur les sources de données du registre. Pour une description complète de ces fonctions, voir [Setup DLL API Reference](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** appelle les fonctions suivantes dans l’installateur DLL pour maintenir les informations de source de données dans le registre:  
  
-   **SQLWriteDSNToIni**. Ajoutez une source de données.  
  
-   **SQLRemoveDSNFromIni**. Supprimer une source de données.  
  
-   **SQLWritePrivateProfileString**. Écrivez une valeur spécifique au conducteur sous un sous-clé de spécification de source de données.  
  
-   **SQLGetPrivateProfileString**. Lisez une valeur spécifique au conducteur à partir d’un sous-clé de spécification de source de données.  
  
-   **SQLGetTranslator**. Invitez l’utilisateur à obtenir un nom et une option de traducteur. Cette fonction appelle **ConfigTranslator** dans la configuration du traducteur DLL.  
  
 La configuration du pilote DLL est écrit par le développeur du conducteur. Il peut faire partie du pilote DLL ou un DLL séparé.
