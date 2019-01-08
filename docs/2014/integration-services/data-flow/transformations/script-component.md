---
title: Composant Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponentdetails.f1
helpviewer_keywords:
- Script transformation
- scripts [Integration Services], transformations
- Script component [Integration Services], about Script component
- Script component [Integration Services]
ms.assetid: 131c2d0c-2e33-4785-94af-ada5c049821e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5db2b6e6467dec58f6a8aa6e6bfc9f105073fbfe
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818028"
---
# <a name="script-component"></a>Composant Script
  Le composant Script héberge le script et permet à un package d'inclure du code de script personnalisé et de l'exécuter. Vous pouvez utiliser le composant Script dans des packages pour :  
  
-   Appliquer plusieurs transformations aux données, au lieu d'utiliser plusieurs transformations dans le flux de données. Par exemple, un script peut ajouter les valeurs de deux colonnes, puis calculer la moyenne de la somme.  
  
-   Accéder aux règles métier dans un assembly .NET existant. Par exemple, un script peut appliquer une règle métier qui spécifie la plage de valeurs correctes dans une colonne `Income`.  
  
-   Utiliser des formules et des fonctions personnalisées en plus des fonctions et des opérateurs fournis par la grammaire des expressions [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Par exemple, validez les numéros de carte de crédit qui utilisent la formule LUHN.  
  
-   Valider les données des colonnes et ignorer les enregistrements contenant des données non valides. Par exemple, un script peut évaluer un montant de frais de port raisonnable et ignorer les enregistrements présentant des montants extrêmement élevés ou bas.  
  
 Le composant Script est un moyen simple et rapide d'inclure des fonctions personnalisées dans un flux de données. Néanmoins, si vous envisagez de réutiliser le code de script dans plusieurs packages, vous devez envisager de programmer un composant personnalisé au lieu d'utiliser le composant Script. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
> [!NOTE]  
>  Si le composant Script contient un script qui essaie de lire la valeur d'une colonne qui est NULL, il échoue lorsque vous exécutez le package. Il est recommandé que votre script utilise la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> pour déterminer si la colonne est NULL avant d’essayer de lire la valeur de la colonne.  
  
 Le composant Script peut être utilisé en tant que source, transformation ou destination. Il prend en charge une entrée et plusieurs sorties. En fonction de l'utilisation qui est faite du composant, il prendra en charge une entrée ou des sorties, ou bien les deux. Le script est appelé par chaque ligne de l'entrée ou de la sortie.  
  
-   Utilisé comme source, le composant Script prend en charge plusieurs sorties.  
  
-   Utilisé comme transformation, le composant Script prend en charge une entrée et plusieurs sorties.  
  
-   Utilisé comme destination, le composant Script prend en charge une entrée.  
  
 Le composant Script ne prend pas en charge les affichages des erreurs.  
  
 Lorsque vous avez décidé que le composant Script est le choix approprié pour votre package, vous devez configurer les entrées et sorties, développer le script que le composant utilise et configurer le composant lui-même.  
  
## <a name="understanding-the-script-component-modes"></a>Présentation des modes du composant Script  
 Dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , le composant Script propose deux modes : le mode Création des métadonnées et le mode Création du code. En mode Création des métadonnées, vous pouvez ajouter et modifier les entrées et les sorties du composant Script, mais vous ne pouvez pas écrire de code. Une fois toutes les entrées et sorties configurées, vous devez basculer en mode Création du code afin d'écrire le script. Le composant Script génère automatiquement le code de base à partir des métadonnées des entrées et des sorties. Si vous modifiez les métadonnées une fois que le composant Script a généré le code de base, votre code risque de ne plus se compiler, car le code de base compilé mis à jour sera peut-être incompatible avec votre code.  
  
## <a name="writing-the-script-that-the-component-uses"></a>Écriture du script utilisé par le composant  
 Le composant Script utilise [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) comme environnement d’écriture des scripts. Vous pouvez accéder à VSTA à partir de **l’Éditeur de transformation de script**. Pour plus d’informations, consultez [Script Transformation Editor &#40;Script Page&#41;](../../script-transformation-editor-script-page.md).  
  
 Le composant Script propose un projet VSTA qui inclut une classe auto-générée, nommée ScriptMain, qui représente les métadonnées du composant. Par exemple, si le composant Script est utilisé en tant que transformation avec trois sorties, ScriptMain inclut une méthode pour chaque sortie. ScriptMain est le point d'entrée dans le script.  
  
 VSTA contient l'ensemble des fonctionnalités standard de l'environnement [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , comme l'éditeur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] à code de couleur, IntelliSense et l'Explorateur d'objets. Le script utilisé par le composant Script est stocké dans la définition du package. Quand vous concevez le package, le code de script est écrit temporairement dans un fichier projet.  
  
 VSTA prend en charge les langages de programmation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic.  
  
 Pour plus d’informations sur la programmation du composant Script, consultez [Extension du flux de données avec le composant Script](script-component.md). Pour obtenir des informations spécifiques sur la configuration du composant Script en tant que source, transformation ou destination, consultez [Développement de types spécifiques de composants Script](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md). Pour obtenir d’autres exemples, notamment une destination ODBC, démontrant l’utilisation du composant Script, consultez [Exemples supplémentaires du composant Script](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
> [!NOTE]  
>  Contrairement aux versions antérieures pour lesquelles il était possible d’indiquer si les scripts étaient précompilés, tous les scripts de [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] et des versions ultérieures sont précompilés. Lorsqu'un script est précompilé, le moteur de langage n'est pas chargé au moment de l'exécution et le package s'exécute plus rapidement. Toutefois, les fichiers binaires précompilés occupent un espace disque important.  
  
## <a name="configuring-the-script-component"></a>Configuration du composant Script  
 Vous pouvez configurer le composant Script de plusieurs manières :  
  
-   Sélectionnez les colonnes d'entrée à référencer.  
  
    > [!NOTE]  
    >  Vous pouvez configurer une seule entrée quand vous utilisez le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
-   Indiquez le script exécuté par le composant.  
  
-   Spécifiez le langage de script  
  
-   Fournissez des listes de variables en lecture seule et en lecture/écrite séparées par des virgules.  
  
-   Ajoutez des sorties supplémentaires, ainsi que des colonnes de sortie auxquelles le script affecte des valeurs.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
### <a name="configuring-the-script-component-in-the-designer"></a>Configuration du composant Script dans le concepteur  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de script**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de transformation de script &#40;page Colonnes d’entrée&#41;](../../script-transformation-editor-input-columns-page.md)  
  
-   [Éditeur de transformation de script &#40;page Entrées et sorties&#41;](../../script-transformation-editor-inputs-and-outputs-page.md)  
  
-   [Éditeur de transformation de script &#40;page Script&#41;](../../script-transformation-editor-script-page.md)  
  
-   [Éditeur de transformation de script &#40;page Gestionnaires de connexions&#41;](../../script-transformation-editor-connection-managers-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
### <a name="configuring-the-script-component-programmatically"></a>Configuration du composant Script par programmation  
 Pour plus d’informations sur les propriétés définissables dans la fenêtre **Propriétés** ou par programmation, cliquez sur l’une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Transformations Integration Services](integration-services-transformations.md)  
  
 [Extension du flux de données avec le composant Script](script-component.md)  
  
  
