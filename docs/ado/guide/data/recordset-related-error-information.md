---
title: Informations sur l’erreur Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3f8e8d9802b5d0c73af73aff20d929c188b9292
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924375"
---
# <a name="recordset-related-error-information"></a>Informations sur les erreurs liées aux recordsets
Au cours de traitement par lots, le **état** propriété de la **Recordset** objet fournit des informations sur les enregistrements individuels dans le **Recordset**. Avant de lancer une mise à jour par lots, le **état** propriété de la **Recordset** reflète les informations sur les enregistrements à ajouter, modifier et supprimer. Après avoir **UpdateBatch** a été appelée, le **état** propriété indique la réussite ou l’échec de l’opération. Lorsque vous passez d’un enregistrement à l’autre le **Recordset**, la valeur de la **état** des modifications de propriété pour décrire l’état de l’enregistrement actif.
