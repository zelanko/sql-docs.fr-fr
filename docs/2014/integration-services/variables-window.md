---
title: Fenêtre Variables | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.variables.f1
helpviewer_keywords:
- Variables Window dialog box
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 23a20f733fd9a6fb2ca3c6e00eb4d1e84b7cb654
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142514"
---
# <a name="variables-window"></a>Fenêtre Variables
  La fenêtre **Variables** permet de créer et de modifier les variables définies par l’utilisateur et d’afficher les variables système.  
  
 Par défaut, la fenêtre **Variables** se trouve sous la zone **Gestionnaires de connexions** du concepteur SSIS, dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Si vous ne voyez pas la fenêtre **Variables** , cliquez sur **Variables** dans le menu **SSIS** pour l'afficher.  
  
 Vous pouvez éventuellement afficher la fenêtre **Variables** en mappant la commande View.Variables avec une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options** .  
  
> [!NOTE]  
>  Les valeurs de la `Name` et `Namespace` propriétés doivent commencer par une lettre de l’alphabet, tel que défini par la norme Unicode 2.0, ou un trait de soulignement (_). Les caractères suivants peuvent être des lettres ou des chiffres, conformément à la convention Unicode standard 2.0, ou un trait de soulignement (\_).  
  
## <a name="options"></a>Options  
 **Ajouter une variable**  
 Ajoutez une variable définie par l'utilisateur.  
  
 **Déplacer la variable**  
 Cliquez sur une variable dans la liste, puis cliquez sur **Déplacer la variable** pour modifier l’étendue de la variable. Dans la boîte de dialogue **Sélectionner une nouvelle étendue** , sélectionnez le package ou un conteneur, une tâche ou un gestionnaire d'événements dans le package pour modifier l'étendue de la variable.  
  
 Pour plus d’informations sur la portée des variables, consultez [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).  
  
 **Supprimer une variable**  
 Sélectionnez une variable dans la liste, puis cliquez sur **Supprimer une variable**.  
  
 **Options de la grille**  
 Cliquez sur cette option pour ouvrir la boîte de dialogue **Options de grille variables** où vous pouvez modifier la sélection des colonnes et appliquer des filtres à la fenêtre **Variables** . Pour plus d'informations, consultez [Options de grille variables](../../2014/integration-services/variable-grid-options.md).  
  
 `Name`  
 Affichez le nom de la variable. Vous pouvez mettre à jour le nom des variables définies par l'utilisateur.  
  
 **Portée**  
 Affichez l'étendue de la variable. Une variable a l'étendue du package entier ou celle d'un conteneur ou d'une tâche. L'étendue de la variable doit être suffisante pour qu'elle soit visible pour tout autre composant ou tâche qui doit lire ou définir ses valeurs.  
  
 Vous pouvez modifier l'étendue en cliquant sur la variable puis en cliquant sur **Déplacer la variable** dans la fenêtre **Variables** .  
  
 **Type de données**  
 Affichez le type de données de la variable. Vous pouvez sélectionner le type de données dans la liste des variables définies par l'utilisateur.  
  
> [!NOTE]  
>  Si vous affectez une expression à la variable, vous ne pouvez pas modifier le type de données.  
  
 **Value**  
 Affichez la valeur de la variable. Vous pouvez mettre à jour la valeur des variables définies par l'utilisateur. Cette valeur peut être un littéral ou une expression. En outre, la valeur peut être une chaîne multiligne. Pour affecter une expression à la variable, cliquez sur le bouton d'ellipse qui est en regard de la colonne **Expression** dans la fenêtre **Variables** .  
  
 `Namespace`  
 Affichez le nom de l'espace de noms. Variables définies par l’utilisateur sont initialement créées dans le **utilisateur** espace de noms, mais vous pouvez modifier le nom de l’espace de noms dans le `Namespace` champ. Pour afficher cette colonne, cliquez sur **Options de la grille**.  
  
 **Déclencher l'événement lorsque la valeur de la variable change**  
 Indiquez si l'événement `OnVariableValueChanged` est déclenché lors de la modification d'une valeur. Vous pouvez mettre à jour la valeur des variables système définies par l'utilisateur. Par défaut, la fenêtre **Variables** ne répertorie pas cette colonne. Pour afficher cette colonne, cliquez sur **Options de la grille**.  
  
 **Description**  
 Affichez la description de la variable. Vous pouvez modifier la description des variables définies par l'utilisateur. Par défaut, la fenêtre **Variables** ne répertorie pas cette colonne. Pour afficher cette colonne, cliquez sur **Options de la grille**.  
  
 **Expression**  
 Affichez l'expression affectée à la variable. Pour affecter une expression, cliquez sur le bouton d'ellipse.  
  
 Si vous affectez une expression à une variable, un marqueur spécial sous la forme d'une icône s'affiche en regard de la variable. Ce marqueur d'icône spécial s'affiche également en regard des gestionnaires de connexions et des tâches contenant des expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’intégration &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)   
 [Utiliser des Variables dans des Packages](../../2014/integration-services/use-variables-in-packages.md)   
 [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)   
 [Générer de fichiers de vidage pour l’exécution des packages](troubleshooting/generating-dump-files-for-package-execution.md)  
  
  