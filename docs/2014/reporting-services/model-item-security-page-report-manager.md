---
title: Page de sécurité (Gestionnaire de rapports) de l’élément de modèle | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.modelproperties.modelitemsecurity.f1
ms.assetid: 8c5b29ae-1f17-41f2-ab59-97899b8fb4fc
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0d7f05024178334c11fccfd819aed1a4f4e023d6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043085"
---
# <a name="model-item-security-page-report-manager"></a>Page Sécurité de l'élément de modèle (Gestionnaire de rapports)
  Utilisez cette page pour sécuriser des parties d'un modèle en accordant ou en refusant des autorisations en lecture seule sur des éléments particuliers. La sécurité de l'élément de modèle affecte l'exploration de données appropriée au moment de l'exécution et la possibilité d'utiliser des parties d'un modèle publié lors de la création de rapports dans le Générateur de rapports. Pour utiliser cette fonctionnalité, vous devez disposer des autorisations de gestionnaire de contenu.  
  
 La sécurité de l'élément de modèle est appliquée à un modèle qui est traité sur le serveur de rapports et n'affecte pas les fichiers .smdl que vous modifiez dans le Générateur de modèles ou utilisez dans le Concepteur de rapports. En outre, celui-ci n'a aucun effet sur les utilisateurs autorisés à modifier une définition de modèle. Un utilisateur qui possède les autorisations de Gestionnaire Contenu ou de Serveur de publication sur un modèle peut consulter toutes les parties de celui-ci, que la sécurité de l'élément de modèle soit appliquée ou non.  
  
> [!NOTE]  
>  La sécurité des éléments de modèle peut être renforcée à l'aide de filtres de sécurité.  
  
 Vous pouvez définir la sécurité de l'élément de modèle sur les entités, dossiers et champs individuels d'un modèle. Dans la mesure où un modèle présente une telle grande surface d'éléments sécurisables, l'héritage des autorisations est intégré au modèle afin que vous puissiez sécuriser un grand nombre d'éléments par le biais d'un nombre relativement restreint d'attributions de rôles. L'héritage des autorisations est basé sur les éléments suivants :  
  
-   Modèle  
  
-   Nœud racine  
  
-   Dossiers ou entités  
  
-   Champs  
  
 Initialement, l'autorisation d'accéder aux éléments de modèle est héritée par le biais des attributions de rôles définies sur le modèle lui-même. Un utilisateur qui a l'autorisation de consulter un modèle dans un dossier dans le Gestionnaire de rapports peut consulter tous les éléments du modèle.  
  
 Si vous appliquez la sécurité de l'élément de modèle, vous devez créer au moins une attribution de rôle au niveau du nœud racine. Cette attribution de rôle initiale au niveau du nœud racine devient la nouvelle source d'autorisations héritées. L'attribution de rôle au niveau du nœud racine est héritée automatiquement par tous les éléments dans la hiérarchie du modèle.  
  
 Pour personnaliser davantage les autorisations sur l'exploration de données, vous pouvez changer les autorisations sur les dossiers et les entités. Enfin, vous pouvez définir des autorisations sur les champs individuels.  
  
 Pour faciliter la gestion des attributions de rôles, définissez des autorisations uniquement sur les dossiers ou entités plutôt que sur les champs individuels. Vous ne pouvez pas effectuer de recherche sur les attributions de rôles que vous avez créées. Si vous définissez la sécurité sur des champs spécifiques et souhaitez ultérieurement mettre à jour les paramètres de sécurité, vous devez parcourir l'espace de noms du modèle pour rechercher les champs que vous avez sécurisés.  
  
 Pour commencer, créez une attribution de rôle au niveau du nœud racine, puis des attributions de rôles supplémentaires sur les entités et les dossiers. Pour supprimer la sécurité de l'élément de modèle, désactivez la case à cocher **Sécuriser les éléments de modèles de manière indépendante pour ce modèle**. La désactivation de la case à cocher rétablit les autorisations initiales héritées du modèle.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a>Pour ouvrir la page Propriétés générales pour un rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le modèle pour lequel vous souhaitez configurer la sécurité pour les éléments de modèle.  
  
2.  Pointez sur le modèle et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page Propriétés générales pour le modèle s'ouvre.  
  
4.  Sélectionnez l'onglet **Sécurité de l'élément de modèle** .  
  
## <a name="options"></a>Options  
 **Sécuriser des éléments de modèles individuels indépendamment pour ce modèle**  
 Activez cette case à cocher pour activer la sécurité des éléments de modèle.  
  
 **Spécifiez le mode de la sécurité pour les éléments de modèles**  
 Affiche tous les éléments d'un modèle. Vous pouvez parcourir l'espace de noms du modèle pour sélectionner l'élément à sécuriser. Vous ne pouvez sélectionner qu'un seul élément à la fois. Veillez à créer la première attribution de rôle au niveau du nœud racine avant de passer aux autres entités et dossiers.  
  
 **Hériter des autorisations de l’élément parent**  
 Sélectionnez cette option pour hériter des paramètres de sécurité de l'élément parent.  
  
 **Affecter une autorisation de lecture pour les utilisateurs et groupes suivants (séparés par des points-virgules)**  
 Sélectionnez cette option pour spécifier le compte d'utilisateur ou de groupe pour lequel vous définissez l'accès. Si vous utilisez la sécurité par défaut, les comptes d'utilisateur et de groupe sont des comptes de domaine Windows. Spécifiez les comptes dans ce format :  *\<domaine >\\< compte\>*.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du serveur de rapports dans Management Studio via la touche F1](tools/report-server-in-management-studio-f1-help.md)  
  
  