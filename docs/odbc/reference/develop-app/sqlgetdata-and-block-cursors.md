---
title: Curseurs SQLGetData et Block | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4841d8d923ff73d187569df3d7f9e29daf0f4e48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107401"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData et curseurs de bloc
**SQLGetData** opère sur une seule colonne d’une seule ligne et ne peut pas extraire un tableau contenant des données de plusieurs lignes. Cela est dû au fait que l’utilisation principale de **SQLGetData** consiste à extraire de longues données en parties, et il y a peu ou pas de raison de le faire pour plusieurs lignes à la fois.  
  
 Pour utiliser **SQLGetData** avec un curseur de bloc, une application appelle d’abord **SQLSetPos** pour positionner le curseur sur une seule ligne. Il appelle ensuite **SQLGetData** pour une colonne dans cette ligne. Toutefois, ce comportement est facultatif. Pour déterminer si un pilote prend en charge l’utilisation de **SQLGetData** avec des curseurs de bloc, une application appelle **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.
