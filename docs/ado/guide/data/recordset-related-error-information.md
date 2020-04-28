---
title: Informations d’erreur liées au recordset | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924375"
---
# <a name="recordset-related-error-information"></a>Informations sur les erreurs liées aux recordsets
Lors du traitement par lots, la propriété **Status** de l’objet **Recordset** fournit des informations sur les enregistrements individuels dans le **Recordset**. Avant qu’une mise à jour par lot ait lieu, la propriété **Status** de l’ensemble d' **enregistrements** reflète des informations sur les enregistrements à ajouter, modifier et supprimer. Une fois la méthode **UpdateBatch** appelée, la propriété **Status** indique la réussite ou l’échec de l’opération. Lorsque vous passez d’un enregistrement à un autre dans le **jeu d’enregistrements**, la valeur de la propriété **Status** change pour décrire l’état de l’enregistrement en cours.
