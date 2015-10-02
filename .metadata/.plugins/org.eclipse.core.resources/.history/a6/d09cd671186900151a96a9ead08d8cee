package com.lastminute;

import java.math.BigDecimal;

public class GenericGoodImpl implements GenericGood {

	private Integer salesTax=Integer.valueOf(10);
	private static final Integer importTax=Integer.valueOf(5);
	private String name;
	private BigDecimal price;
	

	private boolean imported;
	
	public GenericGoodImpl(String name, BigDecimal price, boolean imported) {
		
		this.name=name;
		this.price=price;
		this.imported=imported;

	}
	
	/* (non-Javadoc)
	 * @see com.lastminute.GenericGood#getName()
	 */
	public String getName() {
		return name;
	}	

	/* (non-Javadoc)
	 * @see com.lastminute.GenericGood#getPrice()
	 */
	public BigDecimal getPrice() {
		
		BigDecimal finalPrice=this.price;
		
		if(this.getSalesTax()!=null){
						
			BigDecimal realTax= new BigDecimal((finalPrice.doubleValue()*(this.getSalesTax()+((imported) ? importTax:0)))/100).setScale(2,BigDecimal.ROUND_HALF_UP);			
			int roundTax=(int) (realTax.doubleValue()*100);
			
			while(true)
			{
				if(roundTax%5==0){
					
					finalPrice=finalPrice.add(new BigDecimal((double)roundTax/100).setScale(2, BigDecimal.ROUND_HALF_UP));
					break;
				}
				else{
					
					roundTax+=1;
				}
			}
			
			
			
		}
		
		
		
		return finalPrice;
		
	}
	
	public BigDecimal getTotalTax(){
		
		
		return getPrice().subtract(this.price).setScale(2, BigDecimal.ROUND_HALF_UP);
	}
	public Integer getSalesTax() {
		return salesTax;
	}
	
}
