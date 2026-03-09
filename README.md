---

## 📄 Étape 2 : Rédaction des Manifestes Kubernetes
Vous allez définir trois ressources essentielles dans `apps/todo-api/` :

* [cite_start]**`namespace.yaml`** : Pour isoler votre application[cite: 34].
* [cite_start]**`deployment.yaml`** : Pour définir l'état souhaité (1 replica, image Docker, ressources CPU/RAM)[cite: 39, 48, 59].
    * [cite_start]*Note d'expert* : Si vous n'avez pas d'image prête, utilisez `docker.io/library/nginx:alpine` comme substitut temporaire[cite: 85].
* [cite_start]**`service.yaml`** : Pour exposer l'application en interne (ClusterIP)[cite: 88, 96].

[cite_start]**Publication** : Poussez ces fichiers sur la branche `main` de votre repo GitHub[cite: 105, 108].

---

## ☸️ Étape 3 : Déclaration de l'Application dans ArgoCD
C'est ici que l'on fait le lien entre Git et Kubernetes. [cite_start]Vous pouvez le faire via un fichier `application.yaml` ou l'interface graphique (UI)[cite: 111].

### Configuration clé de l'Application :
* [cite_start]**Source** : Votre URL GitHub et le chemin `apps/todo-api`[cite: 125, 127].
* [cite_start]**Destination** : Le cluster local (`https://kubernetes.default.svc`) et le namespace `todo-api`[cite: 129, 130].
* [cite_start]**SyncPolicy** : Activez l'**Automated Sync**, le **Prune** (supprime ce qui n'est plus dans Git) et le **SelfHeal** (corrige les dérives manuelles)[cite: 132, 133, 134].

**Commande pour appliquer via CLI** :
```bash
kubectl apply -f application.yaml -n argocd
[cite_start]