<script>
  import {
    Col,
    Container,
    Row,
    Card,
    CardBody,
    CardHeader,
    CardFooter,
    CardTitle,
    Input,
    Form,
    FormGroup,
    Label,
    Button
  } from "sveltestrap";

  let product = {
    id: "",
    name: "",
    imageUrl: "",
    description: "",
    category: ""
  };
</script>

<style>

</style>

<main>
  <Container>
    <Row>
      <Col sm="6" mx="auto">
        <Card>
          <CardHeader>
            <CardTitle>Registro Productos</CardTitle>
          </CardHeader>
          <CardBody>
            <Form>
              <FormGroup>
                <Label>Product name</Label>
                <Input
                  placeholder="product name"
                  name="productName"
                  bind:value={product.name} />
              </FormGroup>
              <FormGroup>
                <Label>Product description</Label>
                <Input
                  bind:value={product.description}
                  placeholder="product description"
                  name="productDescription" />
              </FormGroup>
              <FormGroup>
                <Label>imageProduct</Label>
                <Input type="url" placeholder="productUrl" name="productUrl" />
              </FormGroup>
              <FormGroup>
                <Label>Product category</Label>
                <select class="form-control ">
                  <option value="0">product 1</option>
                  <option value="1">product 2</option>
                </select>
              </FormGroup>
              <FormGroup>
                <Button class="btn-success" block size="md">save</Button>
              </FormGroup>
            </Form>
          </CardBody>
        </Card>
      </Col>
    </Row>
  </Container>
</main>
