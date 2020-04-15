---
title: Données de colonnes (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff89566efa65c88325d98422fe17788f27d2c8ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306590"
---
# <a name="column-data"></a>Données de la colonne
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs crée un tampon dans le cache pour chaque tampon de données lié au résultat défini avec **SQLBindCol**. Il utilise les valeurs de ces tampons pour construire une clause **WHERE** lorsqu’elle imite une mise à jour ou une déclaration de suppression positionnée. Il met à jour ces tampons à partir des tampons rowset lorsqu’il récupère les données de la source de données et lorsqu’il exécute des instructions de mise à jour positionnées.  
  
 Lorsque la bibliothèque de curseurs met à jour son cache à partir des tampons rowset, elle transfère les données selon le type de données C spécifié dans **SQLBindCol**. Par exemple, si le type de données C d’un tampon encastré est SQL_C_SLONG, la bibliothèque de curseurs transfère quatre octets de données; s’il s’agit d’SQL_C_CHAR et *BufferLength* est de 10, la bibliothèque de curseurs transfère 10 octets de données. La bibliothèque de curseurs n’effectue aucune vérification ou conversion de type sur les données qu’elle transfère.  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne met pas à jour son cache pour une colonne si*StrLen_or_IndPtr* dans le tampon de rowset correspondant est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC.  
  
 Lorsqu’il met à jour une colonne, une source de données vierges dispose de données de caractère fixes et de données binaires de longueur fixe zero-pads au besoin. Par exemple, une source de données stocke "Smith" dans une colonne CHAR(10) sous le titre "Smith". La bibliothèque de curseurs ne fournit pas de données vierges ou de zéro-pad dans les tampons encastré lorsqu’elle copie ces données à son cache après l’exécution d’une instruction de mise à jour positionnée. Par conséquent, si une application exige que les valeurs dans le cache de la bibliothèque de curseur soient rembourrées ou rembourrées à blanc, elle doit vider ou vider les valeurs dans les tampons encastrés avant d’exécuter une mise à jour positionnée.
