---
title: "DLL d’installation du pilote | Documents Microsoft"
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
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd507929bcb54079f62f81829f5e721834efe21e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="driver-setup-dll"></a>DLL d’installation du pilote
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation du pilote DLL contient le **ConfigDriver** et **ConfigDSN** fonctions. **ConfigDriver** effectue des tâches spécifiques au pilote installation, telles que la saisie des informations spécifiques au pilote dans le Registre. **ConfigDSN** conserve les informations spécifiques au pilote sur les sources de données dans le Registre. Pour obtenir une description complète de ces fonctions, consultez [référence le programme d’installation de l’API DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** appelle les fonctions suivantes dans le programme d’installation pour mettre à jour les informations de source de données dans le Registre DLL :  
  
-   **SQLWriteDSNToIni**. Ajouter une source de données.  
  
-   **SQLRemoveDSNFromIni**. Supprimer une source de données.  
  
-   **SQLWritePrivateProfileString**. Écrire une valeur spécifique au pilote sous une sous-clé de spécification de source de données.  
  
-   **SQLGetPrivateProfileString**. Lire une valeur spécifique au pilote à partir d’une sous-clé de spécification de source de données.  
  
-   **SQLGetTranslator**. Inviter l’utilisateur à un nom de la traduction et une option. Cette fonction appelle **ConfigTranslator** DLL d’installation dans le convertisseur.  
  
 Le programme d’installation du pilote DLL est écrite par le développeur. Il peut faire partie du pilote DLL ou une DLL distincte.
