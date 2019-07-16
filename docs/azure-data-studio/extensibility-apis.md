---
title: API d’extensibilité
titleSuffix: Azure Data Studio
description: En savoir plus sur les API d’extensibilité pour Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 10ebcf94c673df4e8016ae2d0c84d7a5bd89824f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959628"
---
# <a name="azure-data-studio-extensibility-apis"></a>API d’extensibilité Data Studio Azure

[!INCLUDE[name-sos](../includes/name-sos.md)] Fournit une API extensions peuvent utiliser pour interagir avec d’autres parties de Studio de données Azure, telles que l’Explorateur d’objets. Ces API sont disponibles à partir de la [ `src/sql/sqlops.d.ts` ](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.d.ts) de fichiers et sont décrits ci-dessous.

## <a name="connection-management"></a>Gestion des connexions
`sqlops.connection`

### <a name="top-level-functions"></a>Fonctions de niveau supérieur

- `getCurrentConnection(): Thenable<sqlops.connection.Connection>` Obtient la connexion actuelle en fonction de l’éditeur actif ou de la sélection de l’Explorateur d’objets.

- `getActiveConnections(): Thenable<sqlops.connection.Connection[]>` Obtient une liste de connexions de tous les l’utilisateur qui sont actifs. Retourne une liste vide si aucune connexion de ce type.

- `getCredentials(connectionId: string): Thenable<{ [name: string]: string }>` Obtient un dictionnaire qui contient les informations d’identification associées à une connexion. Ils devaient être renvoyées en tant que partie du dictionnaire options sous un `sqlops.connection.Connection` objet mais obtenir sont supprimés de l’objet. 

### `Connection`
- `options: { [name: string]: string }` Le dictionnaire des options de connexion
- `providerName: string` Le nom du fournisseur de connexion (par exemple) « MSSQL »)
- `connectionId: string` L’identificateur unique pour la connexion

### <a name="example-code"></a>Exemple de code
```
> let connection = sqlops.connection.getCurrentConnection();
connection: {
    providerName: 'MSSQL',
    connectionId: 'd97bb63a-466e-4ef0-ab6f-00cd44721dcc',
    options: {
        server: 'mairvine-sql-server',
        user: 'sa',
        authenticationType: 'sqlLogin',
        ...
    },
    ...
}
> let credentials = sqlops.connection.getCredentials(connection.connectionId);
credentials: {
    password: 'abc123'
}

```

## <a name="object-explorer"></a>Explorateur d’objets

`sqlops.objectexplorer`


### <a name="top-level-functions"></a>Fonctions de niveau supérieur
- `getNode(connectionId: string, nodePath?: string): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Obtenir un nœud de l’Explorateur d’objets correspondant à la connexion donnée et le chemin d’accès. Si aucun chemin d’accès n’est fourni, il retourne le nœud de niveau supérieur pour la connexion donnée. Si cela signifie qu’il n’y a aucun nœud à l’emplacement donné, elle retourne `undefined`. Remarque : Le `nodePath` pour un objet est généré par le serveur principal de Service des outils SQL et qu’il est difficile à construire manuellement. Futures améliorations d’API vous permettra d’obtenir les nœuds en fonction des métadonnées que vous fournissez relatives au nœud, telles que le nom, type et le schéma.

- `getActiveConnectionNodes(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Obtenir tous les nœuds de connexion de l’Explorateur d’objets actifs.

- `findNodes(connectionId: string, type: string, schema: string, name: string, database: string, parentObjectNames: string[]): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` Rechercher tous les nœuds de l’Explorateur d’objets qui correspondent aux métadonnées donnée. Le `schema`, `database`, et `parentObjectNames` arguments doivent être `undefined` lorsqu’ils ne sont pas applicables. `parentObjectNames` est une liste d’objets de base de données non parent, du plus élevé au niveau le plus bas dans l’Explorateur d’objets, qui est de l’objet souhaité sous. Par exemple, lors de la recherche pour une colonne « column1 » qui appartient à une table « schema1.table1 » et la base de données « database1 » avec l’ID de connexion `connectionId`, appelez `findNodes(connectionId, 'Column', undefined, 'column1', 'database1', ['schema1.table1'])`. Consultez également le [liste des types pris en charge par Azure Data Studio par défaut](https://github.com/Microsoft/azuredatastudio/wiki/Object-Explorer-types-supported-by-FindNodes-API) pour cet appel d’API.

### <a name="objectexplorernode"></a>ObjectExplorerNode
- `connectionId: string` L’id de la connexion que le nœud existe sous

- `nodePath: string` Le chemin d’accès du nœud, tel qu’utilisé pour un appel à la `getNode` (fonction).

- `nodeType: string` Chaîne représentant le type du nœud

- `nodeSubType: string` Chaîne représentant le sous-type du nœud

- `nodeStatus: string` Chaîne représentant l’état du nœud

- `label: string` L’étiquette du nœud tel qu’il apparaît dans l’Explorateur d’objets

- `isLeaf: boolean` Indique si le nœud est un nœud terminal et a donc pas d’enfants

- `metadata: sqlops.ObjectMetadata` Métadonnées décrivant l’objet représenté par ce nœud

- `errorMessage: string` Message affiché si le nœud est dans un état d’erreur

- `isExpanded(): Thenable<boolean>` Si le nœud est actuellement développé dans l’Explorateur d’objets

- `setExpandedState(expandedState: vscode.TreeItemCollapsibleState): Thenable<void>` Définir si le nœud est développé ou réduit. Si l’état est défini sur None, le nœud ne sera pas modifié.

- `setSelected(selected: boolean, clearOtherSelections?: boolean): Thenable<void>` Définir une valeur indiquant si le nœud est sélectionné. Si `clearOtherSelections` est true, désactivez toutes les autres sélections lors de l’établissement de la nouvelle sélection. Si elle est false, laissez les sélections existantes. `clearOtherSelections` valeur par défaut est true lorsque `selected` est true et false lorsque `selected` a la valeur false.

- `getChildren(): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` Obtenir tous les enfants de nœuds de ce nœud. Retourne une liste vide si aucun enfant n’y.

- `getParent(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Obtient le nœud parent de ce nœud. Retourne un indéfini s’il n’existe aucun parent.

### <a name="example-code"></a>Exemple de code

```cs
private async interactWithOENode(selectedNode: sqlops.objectexplorer.ObjectExplorerNode): Promise<void> {
    let choices = ['Expand', 'Collapse', 'Select', 'Select (multi)', 'Deselect', 'Deselect (multi)'];
    if (selectedNode.isLeaf) {
        choices[0] += ' (is leaf)';
        choices[1] += ' (is leaf)';
    } else {
        let expanded = await selectedNode.isExpanded();
        if (expanded) {
            choices[0] += ' (is expanded)';
        } else {
            choices[1] += ' (is collapsed)';
        }
    }
    let parent = await selectedNode.getParent();
    if (parent) {
        choices.push('Get Parent');
    }
    let children = await selectedNode.getChildren();
    children.forEach(child => choices.push(child.label));
    let choice = await vscode.window.showQuickPick(choices);
    let nextNode: sqlops.objectexplorer.ObjectExplorerNode = undefined;
    if (choice === choices[0]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Expanded);
    } else if (choice === choices[1]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Collapsed);
    } else if (choice === choices[2]) {
        selectedNode.setSelected(true);
    } else if (choice === choices[3]) {
        selectedNode.setSelected(true, false);
    } else if (choice === choices[4]) {
        selectedNode.setSelected(false);
    } else if (choice === choices[5]) {
        selectedNode.setSelected(false, true);
    } else if (choice === 'Get Parent') {
        nextNode = parent;
    } else {
        let childNode = children.find(child => child.label === choice);
        nextNode = childNode;
    }
    if (nextNode) {
        let updatedNode = await sqlops.objectexplorer.getNode(nextNode.connectionId, nextNode.nodePath);
        this.interactWithOENode(updatedNode);
    }
}

vscode.commands.registerCommand('mssql.objectexplorer.interact', () => {
    sqlops.objectexplorer.getActiveConnectionNodes().then(activeConnections => {
        vscode.window.showQuickPick(activeConnections.map(connection => connection.label + ' ' + connection.connectionId)).then(selection => {
            let selectedNode = activeConnections.find(connection => connection.label + ' ' + connection.connectionId === selection);
            this.interactWithOENode(selectedNode);
        });
    });
});
```

## <a name="proposed-apis"></a>API proposées

Nous avons ajouté les API proposées pour autoriser les extensions afficher l’interface utilisateur personnalisée dans les boîtes de dialogue, des Assistants et des onglets de document, entre autres fonctionnalités. Consultez le [fichier de types proposées API](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.proposed.d.ts) pour plus d’informations, mais sachez que ces API est susceptibles d’être modifiées à tout moment. Vous trouverez des exemples montrant comment utiliser certains de ces API dans le [« le service SQL » exemple d’extension](https://github.com/Microsoft/azuredatastudio/tree/master/samples/sqlservices).


