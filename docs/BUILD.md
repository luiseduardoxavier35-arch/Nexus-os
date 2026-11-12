# Build and ISO notes

## Important distinction
BlueBuild customizes and publishes an OCI/bootc image. Producing an installable ISO is a separate media-generation step. A successful image build does not, by itself, prove that an installable ISO exists or boots.

## Initial build approach
1. Review the BlueBuild recipe against the current official schema.
2. Run the GitHub Actions workflow manually.
3. Inspect the full build logs and fix any errors.
4. Confirm that the resulting image is published to the intended container registry.
5. Configure the BlueBuild ISO workflow/tooling for the exact image reference and version.
6. Generate the ISO, record its checksum and test boot in a VM.
7. Only after VM validation, test on the dedicated 480 GB NVMe.

Official references:
- https://blue-build.org/
- https://blue-build.org/reference/recipe/
- https://blue-build.org/reference/cli/
- https://docs.bazzite.gg/

## Disk protection
The 1 TB NVMe contains Windows and must not be formatted or repartitioned. If possible, physically disconnect it during installation tests. The Ryzen 5 5600 has no integrated GPU; keep the RX 7600 installed.
