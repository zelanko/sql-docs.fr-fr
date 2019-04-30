---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 088c9b60861266bf99649343aec2e763097bf155
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198185"
---
# <a name="driver-setup-dll"></a>DLL de configuration de pilote
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation du pilote DLL contient le **ConfigDriver** et **ConfigDSN** fonctions. **ConfigDriver** effectue des tâches spécifiques au pilote installation, comme la saisie des informations spécifiques au pilote dans le Registre. **ConfigDSN** conserve les informations spécifiques au pilote sur les sources de données dans le Registre. Pour obtenir une description complète de ces fonctions, consultez [référence le programme d’installation de l’API DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** appelle les fonctions suivantes dans le programme d’installation DLL à mettre à jour les informations de source de données dans le Registre :  
  
-   **SQLWriteDSNToIni**. Ajouter une source de données.  
  
-   **SQLRemoveDSNFromIni**. Supprimer une source de données.  
  
-   **SQLWritePrivateProfileString**. Écrire une valeur spécifique au pilote dans une sous-clé de spécification de source de données.  
  
-   **SQLGetPrivateProfileString**. Lire une valeur spécifique au pilote à partir d’une sous-clé de spécification de source de données.  
  
-   **SQLGetTranslator**. Invite l’utilisateur pour un nom de la traduction et l’option. Cette fonction appelle **ConfigTranslator** DLL d’installation dans le convertisseur.  
  
 Le programme d’installation du pilote DLL est écrite par le développeur. Il peut faire partie du pilote DLL ou une DLL distincte.
