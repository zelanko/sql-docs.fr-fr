---
title: Anticipation des erreurs | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91741ef8d6b0f7f984958837df3234b0bbc1e009
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472863"
---
# <a name="anticipating-errors"></a>Anticipation des erreurs
Prévention des erreurs est au moins aussi importante que la gestion des erreurs. Cette dernière section contient une liste courte de précautions que votre application peut prendre pour rendre le nombre d’erreurs se produisent.  
  
 Vérifier l’état des objets en vérifiant la valeur le **état** propriété avant d’essayer d’effectuer une opération à l’aide de ces objets. Par exemple, si votre application utilise un global **connexion**, vérifiez son **état** propriété pour voir si elle est déjà ouverte avant d’appeler le **ouvrir** (méthode).  
  
-   N’importe quel programme qui accepte des données à partir d’un utilisateur doit inclure le code pour valider les données avant de les envoyer au magasin de données. Vous ne pouvez pas compter sur le magasin de données, le fournisseur, ADO ou même votre langage de programmation pour vous avertir des problèmes. Vous devez vérifier chaque octet entré par vos utilisateurs, s’assurer que les données sont du type correct pour son champ et que les champs obligatoires ne sont pas vides.  
  
 Vérifiez les données avant d’essayer d’écrire des données dans le magasin de données. Pour ce faire, le plus simple consiste à gérer le **WillMove** événement ou la **WillUpdateRecordset** événement. Pour plus d’informations sur la gestion d’événements ADO, consultez [gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md).  
  
 Assurez-vous que l’option **Recordset** objets ne sont pas au-delà des limites de la **Recordset** avant de déplacer le pointeur d’enregistrement. Si vous essayez de **MoveNext** lorsque **EOF** a la valeur True ou **MovePrev** lorsque **BOF** a la valeur True, une erreur se produit. Si vous effectuez l’une de la **déplacer** méthodes lorsque les deux **EOF** et **BOF** ont la valeur True, une erreur sera générée.  
  
 Erreurs seront produisent si vous essayez d’effectuer des opérations telles que **recherche** et **trouver** sur vide **Recordset**.
