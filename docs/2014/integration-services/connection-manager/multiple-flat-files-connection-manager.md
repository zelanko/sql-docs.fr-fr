---
title: Gestionnaire de connexions de fichiers plats multiples | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 68b9fcf9965a3245b869006d1177104702f8079d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043909"
---
# <a name="multiple-flat-files-connection-manager"></a>Gestionnaire de connexions de fichiers plats multiples
  Un gestionnaire de connexions de fichiers plats multiples permet à un package d'accéder aux données de plusieurs fichiers plats. Par exemple, une source de fichier plat peut utiliser un gestionnaire de connexions de fichiers plats multiples lorsque la tâche de flux de données se trouve dans un conteneur de boucles (conteneur de boucles For, par exemple). Dans chaque boucle du conteneur, la source de fichier plat charge les données à partir du nom de fichier suivant fourni par le gestionnaire de connexions de fichiers plats multiples.  
  
 Lorsque vous ajoutez un gestionnaire de connexions de fichiers plats multiples à un package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui sera converti en une connexion de fichiers plats multiples au moment de l’exécution, définit les propriétés sur le Gestionnaire de connexions de fichiers plats multiples, et Ajoute le Gestionnaire de connexions de fichiers plats multiples à la `Connections` collection du package.  
  
 Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `MULTIFLATFILE`.  
  
 Vous pouvez configurer un gestionnaire de connexions de fichiers plats multiples de plusieurs manières :  
  
-   Spécifiez les fichiers, paramètres régionaux et pages de codes à utiliser. Les paramètres régionaux sont utilisés pour interpréter les données spécifiques à un pays comme les dates, tandis que la page de codes est utilisée pour convertir les données chaînes au format Unicode.  
  
-   Spécifiez le format de fichier. Vous pouvez utiliser un format délimité, à largeur fixe ou en drapeau à droite.  
  
-   Spécifiez une ligne d'en-tête, une ligne de données et des séparateurs de colonnes. Les séparateurs de colonnes peuvent être définis au niveau du fichier et remplacés au niveau de la colonne.  
  
-   Indiquez si la première ligne des fichiers contient les noms de colonnes.  
  
-   Spécifiez un caractère d'identificateur de texte. Chaque colonne peut être configurée pour reconnaître un identificateur de texte.  
  
-   Définissez des propriétés comme le nom, le type de données et la largeur maximale pour des colonnes individuelles.  
  
 Lorsque le gestionnaire de connexions de fichiers plats multiples référence plusieurs fichiers, les chemins d'accès aux fichiers sont séparés par une barre verticale (|). La propriété `ConnectionString` du gestionnaire de connexions utilise le format suivant :  
  
 \<*chemin*>|\<*chemin*>  
  
 Vous pouvez également spécifier plusieurs fichiers en utilisant des caractères génériques. Par exemple, pour la référence de lecteur de tous les fichiers de texte sur le C, la valeur de la `ConnectionString` propriété peut être définie sur C:\\*.txt.  
  
 Si un gestionnaire de connexions de fichiers plats multiples référence plusieurs fichiers, tous les fichiers doivent utiliser le même format.  
  
 Par défaut, le gestionnaire de connexions de fichiers plats multiples définit pour les colonnes de type chaîne une longueur de 50 caractères. Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats multiples** , vous pouvez évaluer des exemples de données et redimensionner automatiquement la longueur de ces colonnes pour empêcher la troncation des données ou la largeur de colonne excessive. Sauf si vous redimensionnez la longueur de colonne dans une source de fichier plat ou une transformation, celle-ci reste la même dans le flux de données. Si ces colonnes mappent dans des colonnes de destination plus étroites, des avertissements apparaissent dans l'interface de l'utilisateur et, à l'exécution, des erreurs peuvent se produire du fait de la troncation des données. Vous pouvez redimensionner les colonnes pour les rendre compatibles avec les colonnes de destination dans le gestionnaire de connexions de fichiers plats multiples, la source du fichier plat ou une transformation. Pour modifier la longueur des colonnes de sortie, vous définissez la `Length` propriété de la colonne de sortie sur le **propriétés d’entrée et sortie** onglet dans le **éditeur avancé** boîte de dialogue.  
  
 Si vous mettez à jour des longueurs de colonne dans le gestionnaire de connexions de fichiers plats multiples après avoir ajouté et configuré la source de fichier plat qui utilise le gestionnaire de connexions, vous n'avez pas à redimensionner manuellement les colonnes de sortie dans la source de fichier plat. Quand vous ouvrez la boîte de dialogue **Source du fichier plat** , la source du fichier plat offre la possibilité de synchroniser les métadonnées de la colonne.  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a>Configuration du gestionnaire de connexions de fichiers plats multiples  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page colonnes&#41;](../multiple-flat-files-connection-manager-editor-columns-page.md)  
  
-   [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page avancé&#41;](../multiple-flat-files-connection-manager-editor-advanced-page.md)  
  
-   [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;afficher un aperçu de la Page&#41;](../multiple-flat-files-connection-manager-editor-preview-page.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Source de fichier plat](../data-flow/flat-file-source.md)   
 [Destination de fichier plat](../data-flow/flat-file-destination.md)   
 [Services d’intégration &#40;SSIS&#41; connexions](integration-services-ssis-connections.md)  
  
  