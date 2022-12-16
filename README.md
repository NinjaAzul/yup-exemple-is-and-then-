# yup-exemple-is-and-then-

```
export const paymentInfoSchema = {
  firstInstallmentPaymentMethod: yup.string().required(required),
  remainingInstallmentPaymentMethod: yup.string().required(required),
  remainingInstallmentPaymentData: yup.object().when('remainingInstallmentPaymentMethod', {
    is: PAYMENT_METHODS.DEBIT,
    then: debitSchema,
  }),
  sendingMethod: yup.number().required(required),
  boletoEmail: yup.number().required(required),
  boletoEmailData: yup.string().when('sendingMethod', {
    is: SENDING_METHODS.EMAIL,
    then: yup.string().when('boletoEmail', {
      is: NEW_OPTIONS.NEW,
      then: yup
        .string()
        .trim()
        .email('Digite um e-mail válido.')
        .required(required),
    }),
  }),
  billingAddress: yup.number().required(required),
  billingAddressData: yup.object().when('billingAddress', {
    is: NEW_OPTIONS.NEW,
    then: addressSchema,
  }),
  returningValuesAccount: yup.number().required(required),
  returningValuesAccountData: yup.object().when('returningValuesAccount', {
    is: NEW_OPTIONS.NEW,
    then: debitSchema,
  }),
}
```
