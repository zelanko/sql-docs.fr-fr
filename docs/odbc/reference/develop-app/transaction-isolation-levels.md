---
title: Niveaux d’isolement des transactions (ODBC) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 622b4cd7f0db259b5ecfd5be63b27df64be965e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298032"
---
# <a name="transaction-isolation-levels-odbc"></a>Niveaux d’isolement des transactions (ODBC)
*Les niveaux d’isolement* des transactions sont une mesure de la mesure dans laquelle l’isolement des transactions réussit. En particulier, les niveaux d’isolement des transactions sont définis par la présence ou l’absence des phénomènes suivants :  
  
-   **Lectures sales** Une *lecture sale* se produit lorsqu’une transaction lit des données qui n’ont pas encore été validées. Supposons, par exemple, que la transaction 1 met à jour une rangée. La transaction 2 lit la ligne mise à jour avant que la transaction 1 n’engage la mise à jour. Si la transaction 1 annule la modification, la transaction 2 aura lu des données qui sont considérées comme n’ayant jamais existé.  
  
-   **Lectures nonrepeatables** Une *lecture nonrepeatable* se produit lorsqu’une transaction lit la même ligne deux fois, mais obtient des données différentes à chaque fois. Par exemple, supposons que la transaction 1 lit une ligne. Transaction 2 met à jour ou supprime cette ligne et engage la mise à jour ou supprimer. Si la transaction 1 relit la ligne, elle récupère différentes valeurs de ligne ou découvre que la ligne a été supprimée.  
  
-   **Fantômes** Un *fantôme* est une ligne qui correspond aux critères de recherche, mais n’est pas initialement vu. Supposons, par exemple, que la transaction 1 lit un ensemble de lignes qui répondent à certains critères de recherche. La transaction 2 génère une nouvelle ligne (par une mise à jour ou un encart) qui correspond aux critères de recherche de la transaction 1. Si la transaction 1 réexamine l’instruction qui lit les lignes, elle obtient un ensemble différent de lignes.  
  
 Les quatre niveaux d’isolement des transactions (tels que définis par SQL-92) sont définis en fonction de ces phénomènes. Dans le tableau suivant, un « X » marque chaque phénomène qui peut se produire.  
  
|Niveau d’isolement des transactions|Lectures sales|Lectures nonrepeatables|Fantômes|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Lecture non validée|X|X|X|  
|Lecture validée|--|X|X|  
|Lecture renouvelable|--|--|X|  
|Sérialisable|--|--|--|  
  
 Le tableau suivant décrit des façons simples qu’un DBMS puisse mettre en œuvre les niveaux d’isolement des transactions.  
  
> [!IMPORTANT]  
>  La plupart des DBMS utilisent des schémas plus complexes que ceux-ci pour accroître la concurrence. Ces exemples ne sont fournis qu’à des fins d’illustration. En particulier, ODBC ne prescrit pas comment certains DBMS isolent les transactions les uns des autres.  
  
|Isolement des transactions|Mise en œuvre possible|  
|---------------------------|-----------------------------|  
|Lecture non validée|Les transactions ne sont pas isolées les unes des autres. Si le DBMS prend en charge d’autres niveaux d’isolement des transactions, il ne tient pas compte du mécanisme qu’il utilise pour mettre en œuvre ces niveaux. De sorte qu’elles n’affectent pas d’autres transactions, les transactions en cours d’exécution au niveau Read Uncommitted sont généralement lus uniquement.|  
|Lecture validée|La transaction attend que les lignes verrouillées par d’autres transactions soient débloquées; cela l’empêche de lire des données « sales ».<br /><br /> La transaction contient un verrou de lecture (si elle ne lit que la ligne) ou écrire le verrou (si elle met à jour ou supprime la ligne) sur la ligne actuelle pour empêcher d’autres transactions de la mettre à jour ou de la supprimer. Les communiqués de transaction lisent les verrous lorsqu’elle se déplace hors de la rangée actuelle. Il contient des serrures d’écriture jusqu’à ce qu’il soit commis ou annulé.|  
|Lecture renouvelable|La transaction attend que les lignes verrouillées par d’autres transactions soient débloquées; cela l’empêche de lire des données « sales ».<br /><br /> La transaction contient des verrous de lecture sur toutes les lignes qu’elle retourne à l’application et écrire des verrous sur toutes les lignes qu’elle insère, met à jour ou supprime. Par exemple, si la transaction comprend la déclaration SQL **SELECT \* FROM Orders**, la transaction lit les lignes de verrouillages que l’application les récupère. Si la transaction comprend la déclaration SQL **DELETE FROM Orders WHERE Status ' 'CLOSED'**, la transaction écrira les lignes au fur et à mesure qu’elle les supprime.<br /><br /> Étant donné que d’autres transactions ne peuvent pas mettre à jour ou supprimer ces lignes, la transaction actuelle évite toute lecture nonrepeatable. La transaction libère ses verrous lorsqu’elle est engagée ou annulée.|  
|Sérialisable|La transaction attend que les lignes verrouillées par d’autres transactions soient débloquées; cela l’empêche de lire des données « sales ».<br /><br /> La transaction contient un verrou de lecture (si elle ne lit que des lignes) ou écrire le verrou (si elle peut mettre à jour ou supprimer des lignes) sur la plage de lignes qu’elle affecte. Par exemple, si la transaction comprend la déclaration SQL **SELECT \* FROM Orders**, la plage est l’ensemble du tableau des commandes; la transaction lue-verrouille la table et ne permet pas d’y insérer de nouvelles lignes. Si la transaction comprend la déclaration SQL **DELETE FROM Orders WHERE Status ' 'CLOSED'**, la gamme est toutes des lignes avec un statut de "CLOSED"; la transaction écrivent-verrouille toutes les lignes dans le tableau des commandes avec un statut de "CLOSED" et ne permet pas d’insérer ou de mettre à jour les lignes de telle sorte que la ligne résultante a un statut de "CLOSED".<br /><br /> Étant donné que d’autres transactions ne peuvent pas mettre à jour ou supprimer les lignes de la plage, la transaction actuelle évite toute lecture nonrepeatable. Étant donné que d’autres transactions ne peuvent pas insérer des lignes dans la plage, la transaction actuelle évite tout fantôme. La transaction libère son verrou lorsqu’elle est engagée ou annulée.|  
  
 Il est important de noter que le niveau d’isolement des transactions n’affecte pas la capacité d’une transaction à voir ses propres changements; les transactions peuvent toujours voir tous les changements qu’elles font. Par exemple, une transaction pourrait consister en deux énoncés **UPDATE,** dont le premier augmente la rémunération de tous les employés de 10 p. 100 et le second fixe le salaire de tous les employés sur un montant maximal à ce montant. Cela ne réussit qu’en tant que seule transaction parce que la deuxième déclaration **UPDATE** peut voir les résultats de la première.
