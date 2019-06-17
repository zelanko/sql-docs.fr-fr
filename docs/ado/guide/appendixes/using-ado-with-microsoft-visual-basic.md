---
title: Utilisation d’ADO avec Microsoft Visual Basic | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, Visual Basic
- Visual Basic [ADO]
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: abbdbeec81a029716ac6516f9436373e91365a23
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702774"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Utilisation d’ADO avec Microsoft Visual Basic et Visual Basic pour Applications
Configuration d’un projet ADO et l’écriture de code ADO sont similaire que vous utilisez Visual Basic ou Visual Basic pour Applications. Cette rubrique aborde l’utilisation d’ADO avec Visual Basic et Visual Basic pour Applications et Remarques éventuelles différences.

## <a name="referencing-the-ado-library"></a>Fait référence à la bibliothèque ADO
 La bibliothèque ADO doit être référencée par votre projet.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Pour référencer ADO à partir de Microsoft Visual Basic

1.  En Visual Basic, à partir de la **projet** menu, sélectionnez **références...** .

2.  Sélectionnez **bibliothèque Microsoft ActiveX Data Objects x.x** dans la liste. Vérifiez qu’au moins les bibliothèques suivantes sont également sélectionnés :

    -   Visual Basic pour Applications

    -   Procédures et les objets de runtime de Visual Basic

    -   Procédures et objets de Visual Basic

    -   OLE Automation

3.  Cliquez sur **OK**.

 Vous pouvez utiliser tout aussi facilement des ADO avec Visual Basic pour Applications, à l’aide de Microsoft Access, par exemple.

#### <a name="to-reference-ado-from-microsoft-access"></a>Pour référencer ADO à partir de Microsoft Access

1.  Dans Microsoft Access, sélectionnez ou créez un module à partir de la **Modules** onglet dans le **base de données** fenêtre.

2.  Sur le **outils** menu, sélectionnez **références...** .

3.  Sélectionnez **bibliothèque Microsoft ActiveX Data Objects x.x** dans la liste. Vérifiez qu’au moins les bibliothèques suivantes sont également sélectionnés :

    -   Visual Basic pour Applications

    -   Bibliothèque d’objets Microsoft Access 8.0 (ou version ultérieure)

    -   Bibliothèque d’objets Microsoft DAO 3.5 (ou version ultérieure)

4.  Cliquez sur **OK**.

## <a name="creating-ado-objects-in-visual-basic"></a>Création d’objets ADO en Visual Basic
 Pour créer une variable automation et une instance d’un objet de cette variable, vous pouvez utiliser deux méthodes : **Dim** ou **CreateObject**.

### <a name="dim"></a>Dim
 Vous pouvez utiliser la **New** mot clé with **Dim** pour déclarer et créer des instances d’objets ADO en une seule étape :

```
Dim conn As New ADODB.Connection
```

 Vous pouvez également le **Dim** instanciation d’objet et de la déclaration d’instruction peut être également deux étapes :

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Il n’est pas nécessaire d’utiliser explicitement le `ADODB` progid avec le **Dim** instruction, en supposant que vous avez référencé correctement la bibliothèque ADO dans votre projet. Il garantit toutefois que vous n’avez pas d’affectation de noms est en conflit avec d’autres bibliothèques.

> [!NOTE]
>  Par exemple, si vous incluez des références aux objets ADO et DAO dans le même projet, vous devez inclure un qualificateur pour spécifier quel modèle d’objet à utiliser lors de l’instanciation **Recordset** objets, comme dans le code suivant :

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 Avec le **CreateObject** instanciation de méthode, la déclaration et l’objet doit être de deux étapes distinctes :

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Les objets instanciés avec **CreateObject** sont à liaison tardive, ce qui signifie qu’ils ne sont pas fortement typés et de fin de ligne de commande est désactivée. Toutefois, il vous autorise à ne pas référencer la bibliothèque ADO à partir de votre projet et vous permet d’instancier des versions spécifiques d’objets. Exemple :

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 Vous pouvez également cela spécifiquement création d’une référence à la bibliothèque de type 2.0 version ADO et la création de l’objet.

 Instanciation d’objets à l’aide de la **CreateObject** méthode est généralement plus lente que l’utilisation de la **Dim** instruction.

## <a name="handling-events"></a>Gestion des événements
 Pour gérer des événements ADO dans Microsoft Visual Basic, vous devez déclarer une variable au niveau du module à l’aide du **WithEvents** mot clé. La variable peut être déclarée uniquement dans le cadre d’un module de classe et doit être déclarée au niveau du module. Pour une discussion plus détaillée de la gestion des événements ADO, consultez [gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md).

## <a name="visual-basic-examples"></a>Exemples Visual Basic
 De nombreux exemples Visual Basic sont incluses dans la documentation ADO. Pour plus d’informations, consultez [exemples de Code ADO dans Microsoft Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>Voir aussi
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) [à l’aide d’ADO avec Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) [à l’aide d’ADO avec les langages de script](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
