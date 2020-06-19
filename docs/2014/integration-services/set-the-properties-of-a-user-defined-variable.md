---
title: Définir les propriétés d’une variable définie par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 53eeb46b5ce23a8976c9de1aaace7959bc708a84
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963079"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>Définir les propriétés d’une variable définie par l’utilisateur
  Pour définir les propriétés d'une variable définie par l'utilisateur dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous pouvez utiliser l'une des fonctionnalités suivantes :  
  
-   Fenêtre Variables.  
  
-   Fenêtre Propriétés. La fenêtre **Propriétés** répertorie les propriétés pour la configuration des variables qui ne sont pas disponibles dans la fenêtre **Variables** : Description, EvaluateAsExpression, Expression, ReadOnly, ValueType et IncludeInDebugDump.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit également un ensemble de variables système dont les propriétés ne peuvent pas être mises à jour, à l’exception de la propriété RaiseChangedEvent.  
  
 **Définition des expressions dans les variables**  
  
 Quand vous utilisez la fenêtre **Propriétés** pour définir des expressions sur une variable définie par l’utilisateur :  
  
-   La valeur d’une variable peut être définie par la propriété Valeur ou la propriété Expression. Par défaut, la propriété EvaluateAsExpression est définie sur `False` et la valeur de la variable est définie par la propriété Value. Pour utiliser une expression pour définir la valeur, vous devez d’abord définir EvaluateAsExpression sur `True` , puis fournir une expression dans la propriété expression. Le résultat de l’évaluation de l’expression est automatiquement affecté à la propriété Valeur.  
  
-   La propriété ValueType contient le type de données de la valeur de la propriété Valeur. Quand Valeur est définie par une expression, ValueType est automatiquement mis à jour avec un type de données compatible avec le résultat de l’évaluation de l’expression. Par exemple, si la valeur contient 0 et que la propriété ValueType contient **Int32** et que vous affectez ensuite à expression la valeur GETDATE (), value contient la date et l’heure actuelles et ValueType a la valeur `DateTime` .  
  
-   La fenêtre **Propriétés** pour la variable permet d’accéder à la boîte de dialogue **Générateur d’expressions** . Vous pouvez utiliser cet outil pour créer, valider et évaluer des expressions. Pour plus d’informations, consultez [Générateur d’expressions](expressions/expression-builder.md) et [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Quand vous utilisez la fenêtre **Variables** pour définir des expressions sur une variable définie par l’utilisateur :  
  
-   Pour utiliser une expression pour définir la valeur de la variable, vérifiez d’abord que le type de données de la variable est compatible avec le résultat de l’évaluation de l’expression, puis fournissez une expression dans la `Expression` colonne de la fenêtre **variables** . La propriété EvaluateAsExpression dans la fenêtre **Propriétés** est automatiquement définie sur `True` .  
  
-   Lorsque vous affectez une expression à une variable, un marqueur spécial sous la forme d'une icône s'affiche en regard de la variable. Ce marqueur d'icône spécial s'affiche également en regard des gestionnaires de connexions et des tâches contenant des expressions.  
  
-   La fenêtre **Variables** pour la variable permet d’accéder à la boîte de dialogue **Générateur d’expressions** . Vous pouvez utiliser cet outil pour créer, valider et évaluer des expressions. Pour plus d’informations, consultez [Générateur d’expressions](expressions/expression-builder.md) et [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Dans la fenêtre **variables** et **Propriétés** , si vous affectez une expression à la variable et `EvaluateAsExpression` que a la valeur `True` , vous ne pouvez pas modifier le type de données de la variable.  
  
 **Définition de l'espace de noms et des propriétés de nom**  
  
 Les valeurs des propriétés `Name` et `Namespace` doivent commencer par une lettre, conformément à la convention Unicode Standard 2.0, ou par un trait de soulignement (_). Les caractères suivants peuvent être des lettres ou des chiffres, conformément à la convention Unicode standard 2.0, ou un trait de soulignement (\_).  
  
## <a name="using-the-variables-window-to-set-properties"></a>Définition de propriétés à l'aide de la fenêtre Variables  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>Pour définir les propriétés d'une variable à l'aide de la fenêtre Variables  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le package pour l'ouvrir.  
  
3.  Dans le menu **SSIS** , cliquez sur **Variables**.  
  
     Vous pouvez éventuellement afficher la fenêtre **Variables** en mappant la commande View.Variables avec une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options** .  
  
4.  Éventuellement, dans la fenêtre **Variables** cliquez sur **Options de la grille**, puis sélectionnez les colonnes qui apparaissent dans la fenêtre **Variables** et sélectionnez les filtres à appliquer à la liste des variables.  
  
5.  Sélectionnez la variable dans la liste, puis mettez à jour les valeurs dans les `Name` colonnes, **type de données**,,, `Value` déclencher la `Namespace` **modification**, **Description** et `Expression` colonnes.  
  
6.  Sélectionnez la variable dans la liste, puis cliquez sur **Déplacer la variable** pour modifier l’étendue.  
  
7.  Pour enregistrer le package mis à jour, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés**.  
  
## <a name="using-the-properties-window-to-set-properties"></a>Définition de propriétés à l'aide de la fenêtre Propriétés  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a>Pour définir les propriétés d'une variable à l'aide de la fenêtre Propriétés  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le package pour l'ouvrir.  
  
3.  Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.  
  
4.  Dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet **Explorateur de package** , puis développez le nœud Package.  
  
5.  Pour modifier les variables avec une portée de package, développez le nœud Variables. Sinon, développez les nœuds Gestionnaires d'événements ou Exécutables jusqu'à ce que vous trouviez le nœud Variables contenant la variable que vous voulez modifier.  
  
6.  Cliquez sur la variable dont vous souhaitez modifier les propriétés.  
  
7.  Dans la fenêtre **Propriétés** , mettez à jour les propriétés en lecture/écriture de la variable. Certaines propriétés sont en lecture/lecture uniquement pour les variables définies par l'utilisateur.  
  
     Pour plus d’informations sur les propriétés, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md).  
  
8.  Pour enregistrer le package mis à jour, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;les variables de&#41; SSIS](integration-services-ssis-variables.md)   
 [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)   
 [Ajouter, supprimer, modifier l'étendue de la variable définie par l'utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
