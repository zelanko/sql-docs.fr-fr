---
title: Problèmes de conception de sécurité ADO | Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, security
ms.assetid: 86b83a38-efdf-4831-a6d5-7e470d517d1c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a879e05e5c2df68058d9351b217382366ae80a0d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52532348"
---
# <a name="ado-security-design-features"></a>Fonctionnalités de conception de sécurité ADO
Les sections suivantes décrivent les fonctionnalités de conception de sécurité dans ActiveX Data Objects (ADO) 2.8 et versions ultérieures. Ces modifications ont été apportées dans ADO 2.8 pour améliorer la sécurité. ADO 6.0, qui est inclus dans Windows DAC 6.0 dans Windows Vista, est fonctionnellement équivalent à ADO 2.8, qui a été inclus dans MDAC 2.8 dans Windows XP et Windows Server 2003. Cette rubrique fournit des informations sur la façon de mieux sécuriser vos applications dans ADO 2.8 ou ultérieure.

> [!IMPORTANT]
>  Si vous mettez à jour votre application à partir d’une version antérieure de ADO, il est recommandé de tester votre application mise à jour sur un ordinateur autre que de production avant de le déployer pour les clients. De cette façon, vous pouvez vous assurer que vous êtes conscient des problèmes de compatibilité avant de déployer votre application mise à jour.

## <a name="internet-explorer-file-access-scenarios"></a>Scénarios d’accès fichier Internet Explorer
 L’effet de fonctionnalités suivant le fonctionnement d’ADO 2.8 et versions ultérieur lorsqu’elle est utilisée dans l’objet de scripts pages Web dans Internet Explorer.

### <a name="revised-and-improved-security-warning-message-box-now-used-to-alert-users"></a>Boîte de message d’avertissement de sécurité améliorées révisée maintenant utilisé pour avertir les utilisateurs
 Pour ADO 2.7 et versions antérieur, le message d’avertissement suivant s’affiche lorsqu’une page Web par script essaie d’exécuter du code ADO à partir d’un fournisseur non approuvé :

```console
This page accesses data on another domain. Do you want to allow this? To
avoid this message in Internet Explorer, you can add a secure Web site to
your Trusted Sites zone on the Security tab of the Internet Options dialog
box.
```

 Pour ADO 2.8 et versions ultérieur, le message précédent n’apparaît plus. Au lieu de cela, le message suivant s’affiche dans ce contexte :

```console
This Website uses a data provider that may be unsafe. If you trust the
Website, click OK, otherwise click Cancel.
```

 Le message précédent permet à l’utilisateur à prendre une décision éclairée, tout en sachant que des conséquences pour ces deux options :

-   Si l’utilisateur approuve le site, en cliquant sur OK permettra de tout le code safe de disque (toutes les méthodes et propriétés ADO à l’exception de l’API accessible de disque décrites plus loin dans cette rubrique) pour exécuter et à exécuter dans la fenêtre du navigateur.

-   Si l’utilisateur n’approuve pas le site, cliquez sur Annuler bloque le code ADO pour accéder aux données à partir de la gestion et l’exécution dans son intégralité.

### <a name="disk-accessible-code-limited-now-to-trusted-sites"></a>Code accessible de disque limité maintenant aux sites approuvés
 Modifications de conception supplémentaires ont été apportées dans ADO 2.8 spécifiquement restreindre la capacité d’un ensemble limité d’API, ce qui risque d’exposer le potentiel pour lire ou écrire dans des fichiers sur l’ordinateur local. Voici les méthodes d’API qui ont été Pluss limité pour la sécurité lors de l’exécution d’Internet Explorer :

-   Pour le ADO **Stream** si l’objet, le [LoadFromFile](../../ado/reference/ado-api/loadfromfile-method-ado.md) ou [SaveToFile](../../ado/reference/ado-api/savetofile-method.md) méthodes sont utilisées.

-   Pour ADO **Recordset** si l’objet, soit la [enregistrer](../../ado/reference/ado-api/save-method.md) (méthode) ou le [Open](../../ado/reference/ado-api/open-method-ado-recordset.md) méthode, par exemple lorsque soit la **adCmdFile** option est définie ou le [fournisseur Microsoft OLE DB persistance (MSPersist)](../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) est utilisé.

 Pour ces ensembles limités des fonctions potentiellement disque accessible, le comportement suivant se produit pour ADO 2.8 et versions ultérieur, si tout code qui utilise ces méthodes est exécuté dans Internet Explorer :

-   Si le site qui a fourni le code a été ajouté précédemment à la liste de la zone Sites de confiance, le code s’exécute dans le navigateur et accéder aux fichiers locaux.

-   Si le site n’apparaît pas dans la liste de la zone Sites de confiance, le code est bloqué et l’accès à des fichiers locaux est refusé.

    > [!NOTE]
    >  Dans ADO 2.8 et versions ultérieur, l’utilisateur n’est pas averti ou recommandé d’ajouter des sites à la liste de la zone Sites de confiance. Par conséquent, la gestion de la liste de Sites de confiance est la responsabilité de ceux qui sont de déploiement ou de prise en charge des applications basées sur le site Web qui requièrent l’accès au système de fichiers local.

### <a name="access-blocked-to-the-activecommand-property-on-recordset-objects"></a>Accès bloqué à la propriété ActiveCommand sur les objets de jeu d’enregistrements
 Lors de l’exécution dans Internet Explorer, ADO 2.8 maintenant bloque l’accès à la [ActiveCommand](../../ado/reference/ado-api/activecommand-property-ado.md) propriété pour un actif **Recordset** de l’objet et retourne une erreur. L’erreur se produit même si la page provient d’un site Web enregistré dans la liste de Sites de confiance.

### <a name="changes-in-handling-for-ole-db-providers-and-integrated-security"></a>Modifications de gestion pour les fournisseurs OLE DB et la sécurité intégrée
 Lors de la révision ADO 2.7 et versions antérieures pour les problèmes de sécurité et problèmes potentiels, le scénario suivant a été découverte :

 Dans certains cas, les fournisseurs OLE DB qui prennent en charge de la sécurité intégrée [DBPROP_AUTH_INTEGRATED](https://msdn.microsoft.com/library/windows/desktop/ms712973.aspx) propriété peut éventuellement permettre à l’aide de scripts de pages Web de réutiliser l’objet de connexion ADO pour se connecter par inadvertance à d’autres serveurs utilise les informations d’identification de connexion actuel des utilisateurs. Pour éviter ce problème, ADO 2.8 et versions ultérieur gèrent les fournisseurs OLE DB en fonction de la façon dont ils ont choisi de fournir ou pas fournir, pour la sécurité intégrée.

 Pour les pages Web qui sont chargés à partir des sites répertoriés dans la liste de la zone Sites de confiance, le tableau suivant fournit une décomposition de la façon dont ADO 2.8 et versions ultérieur gère les connexions ADO dans chaque cas.

|Paramètres d’Internet Explorer pour l’authentification utilisateur, d’ouverture de session|Prend en charge de fournisseur « Integrated Security » et UID et PWD sont spécifiés (SQLOLEDB)|Fournisseur ne prend pas en charge les « Integrated Security » (JOLT, MSDASQL, MSPersist)|Fournisseur prend en charge « Integrated Security » et il est défini sur SSPI (aucun UID/PWD ne sont spécifiés)|
|------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
|Connexion automatique avec le nom d’utilisateur actuel et le mot de passe|Autoriser la connexion|Autoriser la connexion|Autoriser la connexion|
|Invite de nom d’utilisateur et mot de passe|Autoriser la connexion|Échec de connexion|Échec de connexion|
|Connexion automatique uniquement dans la zone Intranet|Autoriser la connexion|Inviter l’utilisateur avec un avertissement de sécurité|Inviter l’utilisateur avec un avertissement de sécurité|
|Ouverture de session anonyme|Autoriser la connexion|Échec de connexion|Échec de connexion|

 Dans le cas où un avertissement de sécurité maintenant s’affiche, la boîte de message informe les utilisateurs :

```console
This Website is using your identity to access a data source. If you trust this Website, click OK, otherwise click Cancel.
```

 Le message précédent permet à l’utilisateur à prendre une décision plus avisée et agissez en conséquence.

> [!NOTE]
>  Pour les sites non approuvés (autrement dit, les sites ne figurant ne pas dans la liste de la zone Sites de confiance), si le fournisseur est également non approuvé (comme nous l’avons vu plus haut dans cette section), l’utilisateur peut voir deux avertissements de sécurité dans une ligne, un avertissement à propos du fournisseur unsafe et de deuxième le Essayez d’utiliser leur identité. Si l’utilisateur clique sur OK pour le premier avertissement, les paramètres d’Internet Explorer et le code de comportement de réponse décrites dans le tableau précédent sont exécutées.

## <a name="controlling-whether-password-text-is-returned-in-ado-connection-strings"></a>Contrôle si le texte du mot de passe est retourné dans les chaînes de connexion ADO
 Lorsque vous essayez d’obtenir la valeur de la [ConnectionString](../../ado/reference/ado-api/connectionstring-property-ado.md) propriété sur ADO **connexion** de l’objet, les événements suivants se produisent :

1.  Si la connexion est ouverte, un appel d’initialisation est effectué pour le fournisseur OLE DB sous-jacent pour obtenir la chaîne de connexion.

2.  En fonction du paramètre dans le fournisseur OLE DB de la [DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO](https://msdn.microsoft.com/library/windows/desktop/ms714905.aspx) propriété, les mots de passe sont inclus, ainsi que d’autres informations de chaîne de connexion qui sont retournées.

 Par exemple, si la propriété dynamique de connexion ADO **Persist Security Info** a la valeur **True**, informations de mot de passe sont incluses dans la chaîne de connexion retournée. Sinon, si le fournisseur sous-jacent a défini la propriété sur **False** (par exemple avec le fournisseur SQLOLEDB), les informations de mot de passe sont omises dans la chaîne de connexion retournée.

 Si vous utilisez un tiers (autrement dit, non Microsoft) fournisseurs OLE DB avec le code de votre application ADO, vous pouvez vérifier comment la **DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO** propriété est implémentée pour déterminer si l’inclusion de informations de mot de passe des chaînes de connexion ADO sont autorisées.

## <a name="checking-for-non-file-devices-when-loading-and-saving-recordsets-or-streams"></a>La vérification pour les appareils non-fichier lors du chargement et l’enregistrement des jeux d’enregistrements ou des flux
 Pour ADO 2.7 et versions antérieur, fichier d’entrée/sortie opérations telles que [Open](../../ado/reference/ado-api/open-method-ado-recordset.md) et [enregistrer](../../ado/reference/ado-api/save-method.md) qui ont été utilisés pour lire et écrire des données de fichiers pourrait permettre dans certains cas un URL ou nom de fichier à utiliser qui a spécifié un disque non- en fonction de type de fichier. Par exemple, LPT1, COM2, PRN. TXT, AUX peut être utilisé comme alias pour l’entrée/sortie entre les imprimantes et les dispositifs auxiliaires sur le système en utilisant certaines

 ADO 2.8 et versions ultérieur, cette fonctionnalité a été mis à jour. Pour ouvrir et enregistrer **Recordset** et **Stream** objets, ADO procède désormais à une vérification de type de fichier pour vous assurer que le périphérique d’entrée ou de sortie spécifié dans un URL ou nom de fichier est un fichier réel.

> [!NOTE]
>  La vérification de type de fichier comme décrit dans cette section s’applique uniquement pour Windows 2000 et versions ultérieures. Il ne s’applique pas aux situations où, ADO 2.8 ou ultérieure s’exécute sous des versions antérieures de Windows, tels que Windows 98.
