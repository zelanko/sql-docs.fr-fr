---
title: Autres méthodes de déplacement dans un Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- Recordset object [ADO], moving
- MovePrevious method [ADO]
ms.assetid: 9f8cf1b2-3def-453f-a0ff-4646c5f15262
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8cb2edebfd0a23f7b626dfdc4cb55eab9684a2c0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700816"
---
# <a name="more-ways-to-move-in-a-recordset"></a>Autres méthodes de déplacement dans un recordset
Les quatre méthodes suivantes servent à déplacer, ou faites défiler, dans le **Recordset**: [MoveFirst, MoveLast, MoveNext et MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md). (Certaines de ces méthodes ne sont pas disponibles sur les curseurs avant uniquement.)  
  
 **MoveFirst** modifie la position actuelle vers le premier enregistrement dans le **Recordset**. **MoveLast** modification de position de l’enregistrement en cours à la dernière de l’enregistrement dans le **Recordset**. Pour utiliser **MoveFirst** ou **MoveLast**, le **Recordset** objet doit prendre en charge les signets ou le déplacement du curseur arrière ; sinon, l’appel de méthode génère une erreur.  
  
 **MoveNext** déplace l’enregistrement actif positionner un seul endroit vers l’avant. Si vous êtes sur le dernier enregistrement lorsque vous appelez **MoveNext**, **EOF** sera défini sur **True**. **MovePrevious** déplace l’enregistrement actif positionner un seul endroit vers l’arrière. Si vous êtes sur le premier enregistrement lorsque vous appelez **MovePrevious**, **BOF** sera défini sur **True**. Il est donc judicieux de vérifier le **EOF** et **BOF** propriétés lors de l’utilisation de ces méthodes et de ramener le curseur vers une position de l’enregistrement active valide si vous dépassez des extrémités de la **Recordset**, comme illustré ici :  
  
```  
. . .  
oRs.MoveNext  
If oRs.EOF Then oRs.MoveLast  
. . .   
```  
  
 Ou, dans le cas de la **MovePrevious** méthode :  
  
```  
. . .   
oRs.MovePrevious  
If oRs.BOF Then oRs.MoveFirst  
. . .  
```  
  
 Dans le cas où le **Recordset** a été filtrée ou triée et les données de l’enregistrement actif sont modifiées, la position peut également changer. Dans ce cas le **MoveNext** méthode fonctionne normalement, mais n’oubliez pas que la position est déplacée d’un enregistrement vers l’avant à partir de la nouvelle position, pas de l’ancien. Par exemple, modifier les données de l’enregistrement en cours, telles que l’enregistrement est déplacé vers la fin de la liste triée **Recordset**, signifie que l’appel **MoveNext** entraîne à ADO de définition de l’enregistrement en cours sur le position après le dernier enregistrement dans le **Recordset** (**EOF** = **True**).  
  
 Le comportement des différentes méthodes de déplacement de la **Recordset** dépend de l’objet, dans une certaine mesure, sur les données dans le **Recordset**. Nouveaux enregistrements ajoutés à la **Recordset** sont initialement ajoutés dans un ordre particulier, ce qui est défini par la source de données et peut-être dépendre, implicitement ou explicitement sur les données dans le nouvel enregistrement. Par exemple, si un tri ou une jointure est effectuée dans la requête qui remplit la **Recordset**, le nouvel enregistrement sera inséré dans l’emplacement approprié dans le **Recordset**. Si le tri n’est pas explicitement spécifié lors de la création du **Recordset**, les modifications dans l’implémentation de source de données peuvent provoquer l’ordre des lignes renvoyées modifier par inadvertance. De plus, le tri, filtrage, fonctions d’édition et de la **Recordset** peuvent affecter l’ordre et éventuellement les lignes dans le jeu d’enregistrements qui seront visibles.  
  
 Par conséquent, **MoveNext**, **MovePrevious**, **MoveFirst**, **MoveLast**, et **déplacer** sont tous respect à d’autres opérations effectuées sur le même **Recordset**. ADO sera toujours tenter de maintenir votre position actuelle jusqu'à ce que vous la déplacez explicitement, mais parfois, les modifications intervenues rendent difficile à comprendre les effets d’un déplacement suivant. Par exemple, si vous appelez **MoveFirst** à la position sur la première ligne d’un objet trié **Recordset** et vous passer du tri par ordre croissant, pour l’ordre décroissant, vous êtes toujours sur la même ligne - mais il est maintenant la dernière ligne dans le **Recordset**. **MoveFirst** vous dirigera vers une autre ligne (la nouvelle première ligne).  
  
 Comme autre exemple, si vous êtes positionné sur une ligne particulière au milieu d’un **Recordset** et que vous appelez **supprimer** , puis appelez **MoveNext**, vous êtes maintenant sur l’enregistrement immédiatement après l’enregistrement supprimé. Toutefois, l’appel **MovePrevious** rend l’enregistrement précédant celle que vous avez supprimé l’enregistrement en cours, car l’enregistrement supprimé n’est plus comptabilisée dans le membre actif de la **Recordset**.  
  
 Il est particulièrement difficile de définir la sémantique de déplacement cohérente entre tous les fournisseurs pour les méthodes qui déplacent par rapport à l’enregistrement en cours - **MovePrevious**, **MoveNext**, et **déplacer** - en cas de modification des données dans l’enregistrement actif. Par exemple, si vous travaillez avec un objet trié, filtrée **Recordset**et vous modifier les données dans l’enregistrement actif afin qu’il serait précéder tous les autres enregistrements, mais vos données modifiées également ne correspond plus au filtre, il n’est ne pas évident où un **MoveNext** opération devrait vous prendre. La conclusion plus sûre est ce mouvement relatif au sein d’un **Recordset** est plus de risques que le déplacement des absolu (telles que l’utilisation **MoveFirst** ou **MoveLast**) lorsque les données sont modification des enregistrements sont modifiées, ajoutés ou supprimés. Tri et filtrage doivent reposer sur une clé primaire ou l’ID, car ce type de valeur ne doit pas modifier.
