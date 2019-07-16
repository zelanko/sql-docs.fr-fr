---
title: Niveaux d’isolement | Microsoft Docs
ms.custom: ''
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
ms.openlocfilehash: 83197b1b487db6c52a8fe9b7a57dd6af55c33571
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985105"
---
# <a name="transaction-isolation-levels"></a>Niveaux d'isolement des transactions
*Niveaux d’isolation de transaction* sont une mesure de l’étendue à quelle transaction isolation réussit. En particulier, les niveaux d’isolement sont définies par la présence ou l’absence des phénomènes suivants :  
  
-   **Lectures de modifications** A *lecture erronée* se produit lorsqu’une transaction lit les données qui n’a pas encore été validées. Par exemple, mises à jour de la transaction 1 une ligne. La transaction 2 lit la ligne mise à jour avant que la transaction 1 valide la mise à jour. Si la transaction 1 annule la modification, la transaction 2 ont lit les données qui sont considéré comme jamais existé.  
  
-   **Lectures non reproductibles** A *lecture non renouvelable* se produit lorsqu’une transaction lit la même ligne à deux reprises, mais Obtient des données différentes chaque fois. Par exemple, transaction 1 lit une ligne. La transaction 2 met à jour ou supprime cette ligne et la mise à jour ou suppression est validée. Si la transaction 1 permet de relire la ligne, il récupère les valeurs de ligne différents ou détecte que la ligne a été supprimée.  
  
-   **Fantômes** A *fantôme* est une ligne qui correspond aux critères de recherche, mais n’est pas initialement visible. Par exemple, supposons que la transaction 1 lit un ensemble de lignes qui répondent à certains critères de recherche. La transaction 2 génère une nouvelle ligne (via une mise à jour ou une instruction insert) qui correspond aux critères de recherche pour la transaction 1. Si la transaction 1 reexecutes l’instruction qui lit les lignes, il obtient un autre ensemble de lignes.  
  
 Les quatre niveaux d’isolement (comme défini par SQL-92) sont définies en termes de ces phénomènes. Dans le tableau suivant, un « X » marque chaque phénomène qui peut se produire.  
  
|Niveau d’isolation de transaction|Lectures de données modifiées|Lectures non reproductibles|Fantômes|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Lecture non validée|X|X|X|  
|Lecture validée|--|X|X|  
|Lecture renouvelable|--|--|X|  
|Sérialisable|--|--|--|  
  
 Le tableau suivant décrit les moyens simples qu’un SGBD peut implémenter les niveaux d’isolation de transaction.  
  
> [!IMPORTANT]  
>  La plupart des SGBD utilisent des schémas plus complexes que ceux-ci pour augmenter la concurrence. Ces exemples sont fournis à titre d’illustration uniquement. En particulier, ODBC n’impose pas de SGBD particulier comment isoler les transactions entre eux.  
  
|Isolation des transactions|Implémentation possible|  
|---------------------------|-----------------------------|  
|Lecture non validée|Les transactions ne sont pas isolées les uns des autres. Si le SGBD prend en charge les autres niveaux d’isolation de transaction, il ignore tout mécanisme qu’il utilise pour implémenter ces niveaux. Afin qu’elles n’affectent pas négativement d’autres transactions, les transactions qui s’exécutent au niveau Read Uncommitted sont généralement en lecture seule.|  
|Lecture validée|La transaction attend que les lignes verrouillé en écriture par d’autres transactions soient déverrouillés ; Cela l’empêche de lire toutes les données « modifiées ».<br /><br /> La transaction contient un verrou de lecture (si elle lit uniquement la ligne) ou l’écriture de verrouillage (si elle met à jour ou supprime la ligne) sur la ligne actuelle pour empêcher d’autres transactions à partir de la mise à jour ou de le supprimer. La transaction libère les verrous en lecture lorsqu’il se déplace hors de la ligne actuelle. Il maintient un verrou d’écriture jusqu'à ce qu’elle est validée ou restaurée.|  
|Lecture renouvelable|La transaction attend que les lignes verrouillé en écriture par d’autres transactions soient déverrouillés ; Cela l’empêche de lire toutes les données « modifiées ».<br /><br /> La transaction maintient un verrou de lecture sur toutes les lignes, qu'elle retourne pour les verrous d’application et d’écriture sur toutes les lignes, il les insertions, mises à jour, ou supprime. Par exemple, si la transaction inclut l’instruction SQL **sélectionnez \* à partir de commandes**, comme l’application extrait les des lignes des transaction des verrouillages en lecture. Si la transaction inclut l’instruction SQL **supprimer à partir de commandes où état = « Fermé »** , les verrous d’écriture transaction lignes comme elle les supprime.<br /><br /> Étant donné que les autres transactions ne peut pas mettre à jour ou supprimer ces lignes, la transaction en cours permet d’éviter les lectures non reproductibles. La transaction libère ses verrous lorsqu’elle est validée ou restaurée.|  
|Sérialisable|La transaction attend que les lignes verrouillé en écriture par d’autres transactions soient déverrouillés ; Cela l’empêche de lire toutes les données « modifiées ».<br /><br /> La transaction maintient un verrou de lecture (si elle lit uniquement les lignes) ou le verrou d’écriture (s’il peut mettre à jour ou supprimer des lignes) sur la plage de lignes qu’il affecte. Par exemple, si la transaction inclut l’instruction SQL **sélectionnez \* à partir de commandes**, la plage est l’ensemble de table Orders ; les transaction des verrouillages en lecture la table et ne pas autoriser toutes les nouvelles lignes à insérer dans celui-ci. Si la transaction inclut l’instruction SQL **supprimer à partir de commandes où état = « Fermé »** , la plage est toutes les lignes avec un état de « Fermé » ; les verrous d’écriture transaction toutes les lignes de commandes de table avec l’état « Fermé » et n’est pas Autoriser toutes les lignes à insérer ou la mise à jour la ligne qui en résulte a le statut « Fermé ».<br /><br /> Étant donné que les autres transactions ne peut pas mettre à jour ou supprimer les lignes de la plage, la transaction en cours permet d’éviter les lectures non reproductibles. Étant donné que les autres transactions ne peut pas insérer des lignes dans la plage, la transaction en cours permet d’éviter les fantômes. La transaction libère son verrou lorsqu’elle est validée ou restaurée.|  
  
 Il est important de noter que le niveau d’isolation de transaction n’affecte pas la possibilité d’une transaction de voir les modifications apportées à son propre ; les transactions peuvent toujours voir toutes les modifications apportées. Par exemple, une transaction peut être constitué de deux **mise à jour** instructions, le premier déclenche le salaire de tous les employés de 10 % et le deuxième définit le salaire de tous les employés sur une valeur maximale de cette quantité. Cette opération réussit comme une transaction unique uniquement, car la deuxième **mise à jour** instruction peut voir les résultats de la première.
