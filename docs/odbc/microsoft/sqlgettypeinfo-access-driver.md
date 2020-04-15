---
title: SQLGetTypeInfo (Chauffeur d’accès) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddfa9bd29f0834adf1c211f9b8a111db0b94d3fe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295149"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans le tableau produit par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sera retournée dans la colonne SEARCHABLE pour les types de données Byte, Counter, Double, Single, Long et Short. (La capacité LIKE peut être atteinte en convertissant la valeur en un personnage en utilisant les fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)
