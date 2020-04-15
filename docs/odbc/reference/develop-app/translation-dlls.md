---
title: Traduction DLLs (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3dad12bcd71434c1013b4fde5b4bd0231e56016f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297944"
---
# <a name="translation-dlls"></a>DLL de translation
L’application et la source de données stockent souvent des données dans différents ensembles de caractères. ODBC fournit un mécanisme générique qui permet au conducteur de traduire des données d’un personnage défini à un autre. Il se compose d’un DLL qui implémente les fonctions de traduction **SQLDriverToDataSource** et **SQLDataSourceToDriver**, qui sont appelés par le conducteur pour traduire toutes les données circulant entre la source de données et le conducteur. Ce DLL peut être écrit par le développeur d’applications, le développeur de pilote, ou un tiers.  
  
 La traduction DLL pour une source de données particulière peut être spécifiée dans les informations du système pour cette source de données; pour plus d’informations, voir [Data Source Specification Subkeys](../../../odbc/reference/install/data-source-specification-subkeys.md). Il peut également être réglé au moment de l’exécution avec les attributs de connexion SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION.  
  
 L’option de traduction est une valeur qui ne peut être interprétée que par une traduction particulière DLL. Par exemple, si la traduction DLL se traduit entre les différentes pages de code, l’option peut donner les numéros des pages de code utilisées par l’application et la source de données. Il n’est pas nécessaire qu’une traduction DLL utilise une option de traduction.  
  
 Une fois qu’une traduction DLL a été spécifiée, le conducteur la charge et l’appelle pour traduire toutes les données circulant entre l’application et la source de données. Cela comprend toutes les déclarations SQL et les paramètres de caractère envoyés à la source de données, et tous les résultats de caractère, métadonnées de caractères tels que les noms de colonnes, et les messages d’erreur récupérés à partir de la source de données. Les données de connexion ne sont pas traduites, car la traduction DLL n’est chargée qu’après que l’application se soit connectée à la source de données.
