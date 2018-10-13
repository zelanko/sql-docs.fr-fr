---
title: Créer un administrateur de domaine - Analytique Platform System | Microsoft Docs
description: Certaines opérations requièrent des privilèges d’administrateur de domaine de système de plateforme d’Analytique. Cette rubrique explique comment créer des administrateurs de domaine de matériel supplémentaires.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 18277b6db2a59c502c4aafbec98974385a4a053d
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168787"
---
# <a name="create-an-aps-domain-administrator"></a>Créer un administrateur de domaine APS
Certaines opérations requièrent des privilèges d’administrateur de domaine de système de plateforme d’Analytique. Cette rubrique explique comment créer des administrateurs de domaine de matériel supplémentaires.  
  
## <a name="create-a-domain-administrator"></a>Créer un administrateur de domaine  
Dispose des autorisations appropriées pour configurer tous les nœuds de points d’accès, l’utilisateur qui exécute le **APS Configuration Manager** (`dwconfig.exe`) doit être un membre de la **Admins du domaine** groupe. Pour démarrer et arrêter les services de points d’accès, l’utilisateur doit être un membre de la **PdwControlNodeAccess** groupe.  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Pour ajouter un utilisateur au groupe Admins du domaine  
  
1.  Journal dans le nœud actif AD **(_appliance\_domaine_-AD01** ou  **_appliance\_domaine_-AD02**) à l’aide d’un compte d’administrateur de domaine appliance existant.  
  
2.  Dans le menu Démarrer, cliquez sur **Exécuter**. Dans le **Open** , tapez **DSA.msc**. Cliquez sur **OK**.  
  
3.  Dans le **Active Directory Users and Computers** programmer, avec le bouton droit **utilisateurs**, pointez sur **New**, puis cliquez sur **utilisateur**.  
  
4.  Dans le **nouvel objet – utilisateur** boîte de dialogue, terminez la description du nouvel utilisateur, puis cliquez sur **suivant**.  
  
    Fermer la boîte de dialogue de mot de passe, puis cliquez sur **suivant**.  
  
    > [!WARNING]  
    > SQL Server PDW ne prend pas en charge le caractère de signe dollar ($) dans l’administrateur de domaine ou les mots de passe d’administrateur local. Un mot de passe contenant un signe dollar est valide et utilisable, mais peut bloquer les activités de mise à niveau et de maintenance  
  
    Confirmer la nouvelle description de l’utilisateur, puis cliquez sur **Terminer**.  
  
5.  Dans la liste des utilisateurs, double-cliquez sur le nouvel utilisateur pour ouvrir la boîte de dialogue de propriétés utilisateur.  
  
6.  Sur le **membre de** , cliquez sur **ajouter**.  
  
    Type **Admins du domaine ; PdwControlNodeAccess** puis cliquez sur **vérifier les noms**. Cliquez sur **OK**.  
  
    Cette opération ajoute le nouvel utilisateur à la **Admins du domaine** groupe et le **PdwControlNodeAccess** groupe. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md)  
  
