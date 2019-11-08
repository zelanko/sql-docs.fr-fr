---
title: Niveaux d’isolation des transactions (ODBC) | Microsoft Docs
ms.custom: seo-dt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- dirty reads [ODBC]
- isolation levels [ODBC]
- nonrepeatable reads [ODBC]
- read uncommitted [ODBC]
- read committed [ODBC]
- serializable reads [ODBC]
- phantoms [ODBC]
- transaction isolation [ODBC]
- repeatable reads [ODBC]
- transactions [ODBC], isolation
ms.assetid: 0d638d55-ffd0-48fb-834b-406f466214d4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e11a0d76fc4a2daece7b6f4f50761d40933792be
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73637213"
---
# <a name="transaction-isolation-levels-odbc"></a>Niveaux d’isolation des transactions (ODBC)
Les *niveaux d’isolation des transactions* sont une mesure de l’étendue de l’isolation des transactions. En particulier, les niveaux d’isolation des transactions sont définis par la présence ou l’absence des phénomènes suivants :  
  
-   **Lectures erronées** Une *lecture incorrecte* se produit lorsqu’une transaction lit des données qui n’ont pas encore été validées. Par exemple, supposons que la transaction 1 met à jour une ligne. La transaction 2 lit la ligne mise à jour avant la validation de la mise à jour par la transaction 1. Si la transaction 1 restaure la modification, la transaction 2 aura des données de lecture qui sont considérées comme n’ayant jamais existé.  
  
-   **Lectures reproductibles** Une *lecture non renouvelable* se produit lorsqu’une transaction lit la même ligne à deux reprises, mais obtient des données différentes à chaque fois. Par exemple, supposons que la transaction 1 Lise une ligne. La transaction 2 met à jour ou supprime cette ligne et valide la mise à jour ou la suppression. Si la transaction 1 relit la ligne, elle récupère des valeurs de ligne différentes ou découvre que la ligne a été supprimée.  
  
-   **Fantômes** Un *fantôme* est une ligne qui correspond aux critères de recherche, mais qui n’est pas visible initialement. Par exemple, supposons que la transaction 1 lise un ensemble de lignes qui répondent à certains critères de recherche. La transaction 2 génère une nouvelle ligne (à l’aide d’une mise à jour ou d’une insertion) qui correspond aux critères de recherche de la transaction 1. Si la transaction 1 Réexécute l’instruction qui lit les lignes, elle obtient un autre ensemble de lignes.  
  
 Les quatre niveaux d’isolation des transactions (tels que définis par SQL-92) sont définis en termes de phénomènes. Dans le tableau suivant, un « X » marque chaque phénomène qui peut se produire.  
  
|Niveau d’isolation de la transaction|Lectures erronées|Lectures reproductibles|Fantômes|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Lecture non validée|X|X|X|  
|Lecture validée|--|X|X|  
|Lecture renouvelable|--|--|X|  
|Serializable|--|--|--|  
  
 Le tableau suivant décrit les méthodes simples d’implémentation des niveaux d’isolation des transactions par un SGBD.  
  
> [!IMPORTANT]  
>  La plupart des SGBD utilisent des schémas plus complexes que ceux-ci pour augmenter la concurrence. Ces exemples sont fournis à titre d’illustration uniquement. En particulier, ODBC ne détermine pas comment des SGBD particuliers isolent les transactions les unes des autres.  
  
|Isolation des transactions|Implémentation possible|  
|---------------------------|-----------------------------|  
|Lecture non validée|Les transactions ne sont pas isolées les unes des autres. Si le SGBD prend en charge d’autres niveaux d’isolation des transactions, il ignore tout mécanisme qu’il utilise pour implémenter ces niveaux. Pour qu’ils n’affectent pas les autres transactions, les transactions qui s’exécutent au niveau READ UNCOMMITTED sont généralement en lecture seule.|  
|Lecture validée|La transaction attend jusqu’à ce que les lignes verrouillées en écriture par d’autres transactions soient déverrouillées ; Cela l’empêche de lire les données « modifiées ».<br /><br /> La transaction maintient un verrou de lecture (si elle lit uniquement la ligne) ou un verrou d’écriture (si elle met à jour ou supprime la ligne) sur la ligne actuelle pour empêcher d’autres transactions de la mettre à jour ou de la supprimer. La transaction libère les verrous en lecture lorsqu’elle quitte la ligne actuelle. Elle contient des verrous d’écriture jusqu’à ce qu’elle soit validée ou annulée.|  
|Lecture renouvelable|La transaction attend jusqu’à ce que les lignes verrouillées en écriture par d’autres transactions soient déverrouillées ; Cela l’empêche de lire les données « modifiées ».<br /><br /> La transaction contient des verrous de lecture sur toutes les lignes qu’elle retourne à l’application et des verrous d’écriture sur toutes les lignes qu’elle insère, met à jour ou supprime. Par exemple, si la transaction comprend l’instruction SQL **SELECT \* from Orders**, la transaction lit-verrouille les lignes lorsque l’application les extrait. Si la transaction comprend l’instruction SQL **Delete dans Orders où Status est « Closed »** , la transaction verrouille les lignes lors de leur suppression.<br /><br /> Étant donné que les autres transactions ne peuvent pas mettre à jour ou supprimer ces lignes, la transaction actuelle évite toute lecture non renouvelable. La transaction libère ses verrous lorsqu’elle est validée ou restaurée.|  
|Serializable|La transaction attend jusqu’à ce que les lignes verrouillées en écriture par d’autres transactions soient déverrouillées ; Cela l’empêche de lire les données « modifiées ».<br /><br /> La transaction maintient un verrou de lecture (si elle lit uniquement les lignes) ou un verrou d’écriture (si elle peut mettre à jour ou supprimer des lignes) sur la plage de lignes qu’elle affecte. Par exemple, si la transaction comprend l’instruction SQL **SELECT \* from Orders**, la plage correspond à la table Orders entière. la transaction verrouille la table et ne permet pas l’insertion de nouvelles lignes. Si la transaction comprend l’instruction SQL **Delete dans Orders où Status est « Closed »** , la plage correspond à toutes les lignes dont l’État est « Closed ». la transaction est verrouillée sur toutes les lignes de la table Orders avec l’État « CLOSEd » et n’autorise pas l’insertion ou la mise à jour de lignes, de sorte que la ligne résultante présente l’État « CLOSEd ».<br /><br /> Étant donné que les autres transactions ne peuvent pas mettre à jour ou supprimer les lignes de la plage, la transaction actuelle évite toute lecture non renouvelable. Étant donné que les autres transactions ne peuvent pas insérer de lignes dans la plage, la transaction en cours évite les fantômes. La transaction libère son verrou lorsqu’elle est validée ou restaurée.|  
  
 Il est important de noter que le niveau d’isolation de la transaction n’affecte pas la capacité d’une transaction à voir ses propres modifications. les transactions peuvent toujours voir les modifications qu’ils effectuent. Par exemple, une transaction peut se composer de deux instructions **Update** , la première déclenchant le paiement de tous les employés de 10 pour cent et le second qui définit le paiement de tous les employés sur une valeur maximale de ce montant. Cela se produit en tant que transaction unique, car la deuxième instruction **Update** peut voir les résultats de la première.
