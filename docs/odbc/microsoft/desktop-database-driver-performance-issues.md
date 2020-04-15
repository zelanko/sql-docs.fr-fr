---
title: Problèmes de performance des pilotes de base de données de bureau (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], performance
- desktop database drivers [ODBC], performance
- Jet-based ODBC drivers [ODBC], performance
ms.assetid: 1a4c4b7e-9744-411f-9b6e-06dfdad92cf7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a819d99a995fd7b287beb66b94f1df526e05f201
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303500"
---
# <a name="desktop-database-driver-performance-issues"></a>Problèmes de performances des pilotes pour les bases de données de poste de travail
Afin d’assurer la compatibilité avec les applications ANSI existantes, les types de données SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR sont exposés comme SQL_CHAR, SQL_VARCHAR et SQL_LONGVARCHAR pour les sources de données Microsoft Access 4.0 ou plus. Les sources de données ne retournent pas les types de données WIDE CHAR, mais les données doivent encore être envoyées à Jet sous forme de Char large. Il est important de comprendre que la conversion aura lieu si un SQL_C_CHAR paramètre ou colonne de résultat est lié à un type de données SQL_CHAR dans une application ANSI.  
  
 Cette conversion peut être particulièrement inefficace en termes de mémoire lorsqu’un type de SQL_C_CHAR est lié à un paramètre de type LONGVARCHAR. Étant donné que le moteur Jet 4.0 n’est pas en mesure de diffuser les données de paramètres LONGTEXT, un tampon de conversion UNICODE doit être attribué deux fois la taille du tampon SQL_C_CHAR ANSI. Le mécanisme le plus efficace est pour l’application d’effectuer la conversion UNICODE et de lier le paramètre comme type SQL_C_WCHAR. Lorsqu’un paramètre est marqué comme une donnée d’exécution et que les données sont fournies lors de plusieurs appels vers SQLPutData, un tampon de données à long texte est cultivé. Une façon d’éviter les frais de croissance de ce tampon "Put Data" est de fournir une longueur facultative via SQL_DATA_AT_EXEC_LEN(x), où *x* est la longueur prévue des octets. Cela va initialiser la taille d’un tampon interne PutData à *x* octets.  
  
> [!NOTE]  
>  Un moyen efficace d’insérer ou de mettre à jour de longues données peut être mis en œuvre à l’aide **de SQLBulkOperations()** ou **SQLSetPos()** et de définir les données longues pour SQL_DATA_AT_EXEC. (EXEC_LEN est ignoré dans ce cas.) Les données peuvent être diffusées en morceaux en appelant **SQLPutData** plusieurs fois, ce qui permettra d’ajouter efficacement les données à la table.  
  
 Lorsqu’une application utilisant une base de données Jet 3.5 via les pilotes microsoft ODBC Desktop Database est mise à niveau vers la version 4.0, une certaine dégradation des performances et une taille accrue de l’ensemble de travail peuvent se produire. C’est parce que quand une version 3. *x* base de données est ouverte en utilisant la nouvelle version 4.0 pilote, il charge Jet 4.0. Lorsque Jet 4.0 ouvre la base de données et voit que la base de données est un 3. *x* version, il charge un pilote ISAM installable qui équivaut à charger le moteur Jet 3.5 ainsi. Pour supprimer la pénalité de performance et de taille, le Jet 3. *x* base de données doit être compacté dans une base de données de format Jet 4.0. Cela permettra d’éliminer le chargement de deux moteurs Jet et de minimiser la trajectoire de code vers les données.  
  
 En outre, le moteur Jet 4.0 est un moteur Unicode. Toutes les chaînes sont stockées et manipulées dans Unicode. Lorsqu’une application ANSI accède à un Jet 3. *x* base de données via le moteur Jet 4.0, les données sont converties de l’ANSI à Unicode et de retour à ANSI. Si la base de données est mise à jour au format version 4.0, les chaînes sont converties en Unicode, supprimant un niveau de conversion des chaînes ainsi que minimisant la trajectoire de code vers les données en passant par un seul moteur Jet.
