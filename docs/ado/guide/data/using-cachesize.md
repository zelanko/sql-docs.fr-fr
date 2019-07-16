---
title: Utilisation de CacheSize | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], CacheSize property
- CacheSize property [ADO]
ms.assetid: ca1c3422-b6a4-4ba6-af55-54f975b698b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2e3a67e9ad0f1f26f804ecb38e960041863fad9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923575"
---
# <a name="using-cachesize"></a>Utilisation de CacheSize
Utilisez le **CacheSize** propriété pour contrôler le nombre d’enregistrements à récupérer en une seule fois dans la mémoire locale à partir du fournisseur. Par exemple, si le **CacheSize** est 10, après la première ouverture du **Recordset** de l’objet, le fournisseur extrait les 10 premiers enregistrements dans la mémoire locale. À mesure que vous parcourez le **Recordset** de l’objet, le fournisseur retourne les données à partir de la mémoire tampon locale. Dès que vous déplacez au-delà du dernier enregistrement dans le cache, le fournisseur récupère les 10 enregistrements suivants à partir de la source de données dans le cache.  
  
> [!NOTE]
>  **CacheSize** est basé sur le **nombre maximal de lignes ouvert** propriété spécifique au fournisseur (dans le **propriétés** collection de la **Recordset** objet). Vous ne pouvez pas définir **CacheSize** à une valeur supérieure à **nombre maximal de lignes ouvert.** Pour modifier le nombre de lignes qui peuvent être ouverts par le fournisseur, définissez **nombre maximal de lignes ouvert**.  
  
 La valeur de **CacheSize** peuvent être ajustés pendant la durée de vie de la **Recordset** objet, mais que la modification de cette valeur affecte uniquement le nombre d’enregistrements dans le cache après les extractions suivantes à partir de la source de données. Modification de la valeur de propriété autonome ne changera pas le contenu actuel du cache.  
  
 S’il existe moins d’enregistrements à récupérer que **CacheSize** Spécifie, le fournisseur renvoie les enregistrements restants et aucune erreur ne se produit.  
  
 Un **CacheSize** paramètre zéro n’est pas autorisée et retourne une erreur.  
  
 Enregistrements récupérés à partir du cache ne reflètent pas les modifications simultanées apportées par d’autres utilisateurs à la source de données. Pour forcer une mise à jour de toutes les données mises en cache, utilisez la [Resync](../../../ado/reference/ado-api/resync-method.md) (méthode).  
  
 Si **CacheSize** a une valeur supérieure à 1, les méthodes de navigation ([déplacer](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext et MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) peut entraîner la navigation vers un élément supprimé enregistrement, si la suppression se produit une fois que les enregistrements ont été récupérés. Après l’extraction initiale, les suppressions suivantes seront répercutées dans votre cache de données jusqu'à ce que vous tentez d’accéder à une valeur de données à partir d’une ligne supprimée. Toutefois, l’affectation **CacheSize** 1 élimine ce problème, car les lignes supprimées ne peuvent pas être extraites.
