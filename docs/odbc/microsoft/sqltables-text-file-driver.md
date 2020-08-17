---
description: SQLTables (pilote de fichier texte)
title: SQLTables (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a6c6f65603cee70811d7c9894ba9d840d28ad4f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339673"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* est null, car aucun des pilotes ne prend en charge les noms de propriétaire. Si *szTableOwner* a la valeur null, toutes les tables sont retournées. La valeur NULL est retournée dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|« TABLE » est le seul type de table pris en charge.<br /><br /> Lorsque le pilote de texte est utilisé, la liste des fichiers retournés par **SQLTables** est déterminée par les extensions de fichier dans la zone de **liste Extensions** de la boîte de dialogue **installation de texte ODBC** .|
