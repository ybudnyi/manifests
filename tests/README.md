# Kustomize Manifest Tests

## Unittests

There are two goals for the unittests:

1. Verify that kustomizations are applied correctly (kubeflow/manifests#1014)
1. Verify that various conventions are enforced (kubeflow/manifests#1015)

### Verifying Kustomizations Are Applied Correctly

Examples of kustomizations that we would like to verify are applied and generate the expected output

<<<<<<< HEAD
* Patches
* Variable substitution
* Composition of resources
=======
**To use KFserving v0.5/0.6 instead of KServe v0.7, comment the 6,7th lines and uncomment the 10,11th lines here [e2e/utils/kserve.py](https://github.com/kubeflow/manifests/compare/master/tests/e2e/utils/kserve.py#L6-L11)**

The e2e tests are completely independent of the underlying K8s cluster, as well
as the platform of the cluster. These tests should be able to run in real
world clusters, as well as ephemeral ones like KinD.
>>>>>>> v1.6.0

The general approach to doing this is

1. Check in one more "kustomization.yaml" files corresponding to test cases
1. Run "kustomize build -o ..." and check in the output as the expected test output

   * Reviewers can verify changes to the expected output to ensure changes have the desired effect on the expected output
1. Unittests run "kustomize build" and compare output to expected output to ensure kustomize packages are in sync with the expected output
1. Make commands make it easy to regenerate the expected output as part of a change.

   ```
   cd tests
   make generate-changed-only
   ```