---
title: Créer, supprimer ou modifier un rôle (Management Studio) | Microsoft Docs
ms.date: 05/07/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f079b7b16f485b92c60952d082281a1dba52d024
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65570547"
---
# <a name="role-definitions---create-delete-or-modify"></a>Définitions de rôles - créer, supprimer ou modifier

Reporting Services fournit des rôles prédéfinis qui établissent des niveaux d’accès au serveur de rapports. Chaque utilisateur ou groupe qui nécessite l’accès au serveur de rapports se voit attribuer un rôle qui définit les tâches autorisées. Les rôles sont définis pour l'ensemble du serveur de rapports. Vous devez être cohérent quant à la manière dont un rôle est défini et utilisé dans tous domaines d’opération du serveur de rapports.

Pour créer, modifier ou supprimer des rôles, vous pouvez utiliser [!INCLUDE[SQL Server Management Studio](../../includes/ssmanstudiofull-md.md)]. Vous pouvez supprimer seulement les rôles qui ne sont pas utilisés.

 Pour attribuer les rôles que vous créez à des utilisateurs et des groupes, utilisez le portail web SSRS. Pour plus d’informations, consultez [Accorder à un utilisateur l’accès à un serveur de rapports](../../reporting-services/security/grant-user-access-to-a-report-server.md).

> [!NOTE]  
>Si le serveur de rapports est configuré en mode intégré SharePoint, et si vous vous êtes connecté au site SharePoint auquel le serveur de rapports est intégré, vous pouvez afficher et modifier les niveaux d'autorisation qui contrôlent l'accès au contenu et aux opérations du serveur de rapports.

## <a name="to-create-a-role-definition"></a>Pour créer une définition de rôle

1. Dans l'Explorateur d'objets, développez un nœud du serveur de rapports.

2. Développez le dossier Sécurité.

3. Si vous créez une définition de rôle au niveau élément, cliquez avec le bouton droit sur **Rôles** > **Nouveau rôle**.

    Ou si vous créez une définition de rôle au niveau système, cliquez avec le bouton droit sur **Rôles système** > **Nouveau rôle système**.

4. Tapez un nom unique pour le rôle. Il doit contenir au moins un caractère. Il peut également comprendre des espaces et certains symboles, à l’exception des caractères suivants `[; : \ / @ & = + , $ / * < > | "]`.

5. Tapez éventuellement une description. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], cette description n’est visible que dans cette page. Les utilisateurs qui voient cet élément par le biais du portail web peuvent voir la description dans cet outil.

6. Sélectionnez les tâches pouvant être effectuées par les membres de ce rôle.

7. Sélectionnez **OK**.

### <a name="to-delete-or-modify-a-role-definition"></a>Pour supprimer ou modifier une définition de rôle  

1. Dans l'Explorateur d'objets, développez un nœud du serveur de rapports.

2. Développez le dossier Sécurité.

3. Pour supprimer ou modifier une définition de rôle au niveau d’un élément, développez le dossier Rôles, puis effectuez l’une des actions suivantes :

    1. Pour supprimer une définition de rôle, cliquez avec le bouton droit sur l’élément > **Supprimer**. La boîte de dialogue **Suppression des éléments du catalogue** s’affiche. Sélectionnez **OK** pour supprimer le rôle.
  
    2. Pour modifier une définition de rôle, cliquez avec le bouton droit sur l’élément > **Propriétés**. La page Général de la boîte de dialogue **Propriétés de rôle d’utilisateur** s’affiche.

         Sélectionnez les tâches que les membres de ce rôle peuvent effectuer, puis sélectionnez **OK**.
  
4. Pour supprimer ou modifier une définition de rôle au niveau d’un système, développez le dossier **Rôles système** . Effectuez l’une des actions suivantes :

- Pour supprimer une définition de rôle système, cliquez avec le bouton droit sur l’élément, puis sélectionnez **Supprimer**. La boîte de dialogue **Suppression des éléments du catalogue** s’affiche. Sélectionnez **OK** pour supprimer le rôle.

- Pour modifier une définition de rôle système, cliquez avec le bouton droit sur l’élément, puis sélectionnez **Propriétés**. La page Général de la boîte de dialogue **Propriétés de rôle système** s’affiche. Sélectionnez les tâches que les membres de ce rôle peuvent effectuer, puis sélectionnez **OK** pour appliquer les modifications.

## <a name="see-also"></a>Voir aussi

 [Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)  
 [Créer et gérer des attributions de rôles](../../reporting-services/security/create-and-manage-role-assignments.md)  
 [Reporting Services pour SQL Server Management Studio &#40;SSRS&#41;](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)
