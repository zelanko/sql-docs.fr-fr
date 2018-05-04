---
title: DLL de traduction | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22db3f197d51a55c094ffad6a6c821da250efa89
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="translation-dlls"></a>DLL de traduction
L’application et la source de données stockent souvent des données dans plusieurs jeux de caractères. ODBC fournit un mécanisme générique qui permet au pilote de convertir les données d’un jeu de caractères à un autre. Il se compose d’une DLL qui implémente les fonctions de conversion **SQLDriverToDataSource** et **SQLDataSourceToDriver**, qui sont appelé par le pilote à traduire toutes les données circulent entre la source de données et le pilote. Cette DLL peuvent être écrites par le développeur d’applications, le développeur de pilotes, ou un tiers.  
  
 La DLL de traduction pour une source de données particulier peut être spécifiée dans les informations système pour cette source de données ; Pour plus d’informations, consultez [sous-clés de spécification de Source de données](../../../odbc/reference/install/data-source-specification-subkeys.md). Elle peut également être définie au moment de l’exécution avec les attributs de connexion SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION.  
  
 L’option de traduction est une valeur qui peut être interprétée uniquement par une DLL de traduction particulière. Par exemple, si la traduction DLL traduit entre les pages de codes différentes, l’option peut donner les numéros des pages de codes utilisées par l’application et la source de données. Il n’existe aucune spécification pour une DLL de traduction d’utiliser une option de traduction.  
  
 Après une traduction que DLL a été spécifié, le pilote charge et appelle pour convertir toutes les données transitant entre l’application et la source de données. Cela inclut toutes les instructions SQL et les paramètres de caractères envoyés à la source de données et tous les résultats de caractères, les métadonnées de caractères tels que les noms de colonnes et les messages d’erreur sont récupérées à partir de la source de données. Données de connexion ne sont pas traduites, étant donné que la DLL de traduction n’est pas chargée tant qu’après que l’application est connectée à la source de données.
