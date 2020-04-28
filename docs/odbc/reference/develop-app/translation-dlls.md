---
title: Dll de traduction | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297944"
---
# <a name="translation-dlls"></a>DLL de translation
L’application et la source de données stockent souvent des données dans différents jeux de caractères. ODBC fournit un mécanisme générique qui permet au pilote de convertir les données d’un jeu de caractères à un autre. Il se compose d’une DLL qui implémente les fonctions de traduction **SQLDriverToDataSource** et **SQLDataSourceToDriver**, qui sont appelées par le pilote pour traduire toutes les données circulant entre la source de données et le pilote. Cette DLL peut être écrite par le développeur de l’application, le développeur du pilote ou un tiers.  
  
 La DLL de traduction pour une source de données particulière peut être spécifiée dans les informations système de cette source de données ; Pour plus d’informations, consultez [sous-clés de spécification de source de données](../../../odbc/reference/install/data-source-specification-subkeys.md). Elle peut également être définie au moment de l’exécution avec les attributs de connexion SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION.  
  
 L’option de traduction est une valeur qui peut être interprétée uniquement par une DLL de traduction particulière. Par exemple, si la DLL de traduction se traduit par des pages de codes différentes, l’option peut fournir les numéros des pages de codes utilisées par l’application et la source de données. Il n’est pas nécessaire qu’une DLL de traduction utilise une option de traduction.  
  
 Une fois qu’une DLL de traduction a été spécifiée, le pilote la charge et l’appelle pour traduire toutes les données circulant entre l’application et la source de données. Cela comprend toutes les instructions SQL et les paramètres de caractères envoyés à la source de données, ainsi que tous les résultats de caractères, les métadonnées de caractères, telles que les noms de colonnes, et les messages d’erreur récupérés à partir de la source de données. Les données de connexion ne sont pas traduites, car la DLL de traduction n’est pas chargée tant que l’application n’a pas été connectée à la source de données.
